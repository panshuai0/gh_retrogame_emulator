JNI_INCLUDE = -I/usr/include/classpath

CC = /opt/mipsel-linux-uclibc/usr/bin/mipsel-linux-gcc
CFLAGS = $(JNI_INCLUDE) -Os -mips32 -mtune=mips32 -mno-mips16 -mbranch-likely -pipe -G0 -fno-common -fpeel-loops
LDFLAGS = -s

SOURCES = java_nio_ByteBufferImpl.c

OBJECTS = $(patsubst %.c, %.o, $(SOURCES))

all: libmidpathnio.so

%.o : %.c
	$(CC) $(CFLAGS) -fPIC -g -c -Wall -o $(patsubst %.c, %.o, $<) $<

%.so: $(OBJECTS)
	$(CC) $(LDFLAGS) -shared -Wl,-soname,$@ -lc -o $@ $^

clean:
	rm -f *.so *.o 



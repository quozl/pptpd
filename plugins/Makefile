CC	= gcc
COPTS	= -O2 -g
CFLAGS	= $(COPTS) -I.. -I../../include -fPIC
LDFLAGS	= -shared
INSTALL	= install -o root

PLUGINS := pptpd-logwtmp.so

# include dependencies if present
ifeq (.depend,$(wildcard .depend))
include .depend
endif

all:	$(PLUGINS)

%.so: %.c
	$(CC) -o $@ $(LDFLAGS) $(CFLAGS) $^

LIBDIR	= $(DESTDIR)/usr/lib/pptpd/

install: $(PLUGINS)
	$(INSTALL) -d $(LIBDIR)
	$(INSTALL) $? $(LIBDIR)

uninstall:
	rm -f $(LIBDIR)$(PLUGINS)

clean:
	rm -f *.o *.so *.a

depend:
	$(CPP) -M $(CFLAGS) *.c >.depend
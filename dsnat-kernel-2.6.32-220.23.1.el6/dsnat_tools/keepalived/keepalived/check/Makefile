# Makefile
#
# Keepalived OpenSource project.
#
# Copyright (C) 2001-2011 Alexandre Cassen, <acassen@linux-vs.org>

KERNEL   = _KRNL_2_6_
CC	 = gcc
INCLUDES = -I../include -I../../lib
CFLAGS	 = -g -O2  -I/lib/modules/2.6.32-220.23.1.el6.xiaomi.x86_64/build/include $(INCLUDES) \
	   -Wall -Wunused -Wstrict-prototypes
DEFS	 = -D$(KERNEL) -D_WITH_LVS_ -D_HAVE_IPVS_SYNCD_ -D_WITH_VRRP_ 
COMPILE	 = $(CC) $(CFLAGS) $(DEFS)

OBJS = 	check_daemon.o check_data.o check_parser.o \
	check_api.o check_tcp.o check_http.o check_ssl.o \
	check_smtp.o check_misc.o ipwrapper.o ipvswrapper.o

HEADERS = $(OBJS:.o=.h)

.c.o:
	$(COMPILE) -c $<

all:	$(OBJS)

clean:
	rm -f *.a *.o *~

distclean: clean
	rm -f Makefile

check_daemon.o: check_daemon.c ../include/check_daemon.h \
  ../include/check_parser.h ../include/check_data.h ../include/check_api.h \
  ../include/global_data.h ../include/ipwrapper.h ../include/ipwrapper.h \
  ../include/pidfile.h ../include/daemon.h ../../lib/list.h ../../lib/memory.h \
  ../../lib/parser.h ../../lib/signals.h ../include/vrrp_netlink.h \
  ../include/vrrp_if.h
check_data.o: check_data.c ../include/check_data.h \
  ../include/check_api.h ../../lib/memory.h ../../lib/utils.h
check_parser.o: check_parser.c ../include/check_parser.h \
  ../include/check_data.h ../include/check_api.h ../include/global_data.h \
  ../include/global_parser.h ../../lib/parser.h ../../lib/memory.h \
  ../../lib/utils.h
check_api.o: check_api.c ../include/check_api.h ../../lib/parser.h \
  ../../lib/memory.h ../../lib/utils.h ../include/check_misc.h \
  ../include/check_tcp.h ../include/check_http.h ../include/check_ssl.h
check_tcp.o: check_tcp.c ../include/check_tcp.h ../include/check_api.h \
  ../../lib/memory.h ../include/ipwrapper.h ../include/layer4.h \
  ../include/smtp.h ../../lib/utils.h ../../lib/parser.h
check_http.o: check_http.c ../include/check_http.h ../include/check_ssl.h \
  ../include/check_api.h ../../lib/memory.h ../../lib/parser.h \
  ../../lib/utils.h
check_ssl.o: check_ssl.c ../include/check_ssl.h ../include/check_api.h \
  ../../lib/memory.h ../../lib/parser.h ../include/smtp.h \
  ../../lib/utils.h
check_smtp.o: check_smtp.c ../include/check_smtp.h ../include/check_api.h \
  ../../lib/memory.h ../include/ipwrapper.h ../include/smtp.h \
  ../../lib/utils.h ../../lib/notify.h ../../lib/parser.h ../include/daemon.h
check_misc.o: check_misc.c ../include/check_misc.h ../include/check_api.h \
  ../../lib/memory.h ../include/ipwrapper.h ../include/smtp.h \
  ../../lib/utils.h ../../lib/notify.h ../../lib/parser.h ../include/daemon.h
ipwrapper.o: ipwrapper.c ../include/ipwrapper.h ../../lib/memory.h \
  ../../lib/utils.h ../../lib/notify.h
ipvswrapper.o: ipvswrapper.c ../include/ipvswrapper.h ../../lib/utils.h \
  ../../lib/memory.h

---
title: "Create a new user"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by rogue417 on 2007-02-23
I am trying to run a deamon which is started by the following script:

```
#!/bin/sh
#
# Copyright (c) 2005 Messiah College.

DKFILTERUSER=dkfilter
DKFILTERGROUP=dkfilter
DKFILTERDIR=/usr/local/dkfilter

HOSTNAME=`hostname -f`
DOMAIN=`hostname -d`
DKFILTER_IN_ARGS="--hostname=$HOSTNAME 127.0.0.1:10025 127.0.0.1:10026"
DKFILTER_OUT_ARGS="--keyfile=$DKFILTERDIR/private.key --selector=postfix --domain=$DOMAIN --method=nofws --headers 127.0.0.1:10027 127.0.0.1:10028"

DKFILTER_IN_BIN="$DKFILTERDIR/bin/dkfilter.in"
DKFILTER_OUT_BIN="$DKFILTERDIR/bin/dkfilter.out"
PIDDKFILTER_IN="/var/run/dkfilter.in"
PIDDKFILTER_OUT="/var/run/dkfilter.out"

case "$1" in
        start)
                echo -n "Starting inbound DomainKeys-filter (dkfilter.in)..."

                start-stop-daemon --start -q -p$PIDDKFILTER_IN -u $DKFILTERUSER -g $DKFILTERGROUP -x `$DKFILTER_IN_BIN $DKFILTER_IN_ARGS`
                RETVAL=$?
                if [ $RETVAL -eq 0 ]; then
                        echo done.
                else
                        echo failed.
                        exit $RETVAL
                fi
                echo -n "Starting outbound DomainKeys-filter (dkfilter.out)..."
                 start-stop-daemon --start -q -p $PIDDKFILTER_OUT -u $DKFILTERUSER -g $DKFILTERGROUP -x `$DKFILTER_OUT_BIN $DKFILTER_OUT_ARGS` &
                RETVAL=$?
                if [ $RETVAL -eq 0 ]; then
                        echo done.
                else
                        echo failed.
                        exit $RETVAL
                fi
                ;;

        stop)
                echo -n "Shutting down inbound DomainKeys-filter (dkfilter.in)..."
                 start-stop-daemon --stop -p $PIDDKFILTER_IN
                RETVAL=$?
                if [ $RETVAL -eq 0 ]; then
                        echo done.
                else
                        echo failed.
                fi
                echo -n "Shutting down outbound DomainKeys-filter (dkfilter.out)..."
                start-stop-daemon --stop -p $PIDDKFILTER_OUT
                RETVAL=$?
                if [ $RETVAL -eq 0 ]; then
                        echo done.
                else
                        echo failed.
                        exit $RETVAL
                fi
                ;;
        restart)
                $0 stop
                $0 start
                ;;
        *)
                echo "Usage: $0 {start|stop|restart}"
                exit 1
                ;;
esac
```

When I run /etc/init.d/dkfilter start I get the following:

```
user@postman:~$ sudo /etc/init.d/dkfilter start
Password:
Starting inbound DomainKeys-filter (dkfilter.in)...Becoming sub class of "Net::Server::PreFork"
2007/02/23-09:59:11 main (type MySmtpProxyServer) starting! pid(6068)
Binding to TCP port 10025 on host 127.0.0.1
Group Not Defined.  Defaulting to EGID '0 0'
User Not Defined.  Defaulting to EUID '0'
```
 
I know I dont want to run this daemon as root so I want to create a new user called dkfilter but I do not know how to create a new user or what privileges to give it.

Any thought?

---

### Post by IYY on 2007-02-23
I don't know if this will help, but a new use can be added with

```
sudo adduser dkfilter
```

---

### Post by rogue417 on 2007-02-23
Cool... That lets me creat the user... Now i just need to know which group to put it in or which permissions.. Thanks!

---

### Post by stcorbett on 2008-04-20
Did you end up getting it working?

I think I'm at the same place:

```
/etc/init.d/dkfilter start
Starting inbound DomainKeys-filter (dkfilter.in)...Becoming sub class of "Net::Server::PreFork"
2008/04/20-14:03:40 main (type MySmtpProxyServer) starting! pid(11290)
Binding to TCP port 10025 on host 127.0.0.1
Group Not Defined.  Defaulting to EGID '100 107 106 100'
User Not Defined.  Defaulting to EUID '1000'
```

Email isn't getting filtered however....  What step did you need to take after getting that error?

---


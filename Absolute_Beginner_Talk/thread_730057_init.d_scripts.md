---
title: "init.d scripts"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by medha on 2008-03-20
I have an init.d script to start blktrace at system boot, which looks like this:

#! /bin/sh

SUFFIX=`date +%s`
DEVICE=/dev/sda
HOSTNAME="$(cat /etc/hostname)"

do_start () {
        echo "Starting blktrace..."
        blktrace -d $DEVICE -o "/tmp/$HOSTNAME-$SUFFIX"
        echo "Done"
}
case "$1" in
  start|"")
        do_start
        ;;
  restart|reload|force-reload)
       echo "Error: argument '$1' not supported" >&2
       exit 3
       ;;
 stop)
       # No-op
       ;;
 *)
       echo "Usage: start-blktrace.sh [start|stop]" >&2
       exit 3
       ;;
esac

When I try to execute it using: sudo /etc/init.d/start-blktrace.sh
I get the following error:
$ sudo /etc/init.d/start-blktrace.sh
Starting blktrace...
./tmp/rmga2-1206037731.blktrace.0: No such file or directory
Failed to start worker threads
Done


What am I doing wrong? Why does it try to look for a ./tmp instead of a /tmp/?

---

### Post by original_jamingrit on 2008-03-20
the '.' refers to the current directory, so it's trying to find tmp/ withing the current working directory.

---

### Post by spiderbatdad on 2008-03-20
thinking the correct syntax would be:```
sudo /etc/init.d/blktrace start
```

---


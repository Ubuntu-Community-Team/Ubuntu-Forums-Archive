---
title: "Run Levels / Startup Scripts"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by kaptainlange on 2006-04-27
Hello, I have just switched my personal ftp/www/mysql/storage server from FreeBSD to Linux.  Why?  I've never used Linux in a server environment and wanted to give it a try.  Anyways, I am running into difficulties figuring out exactly how runlevels work.  My current problem is that my web server is not starting up automatically.  I look in my /etc/init.d and I see a script to start it up, however no dice when I reboot.  I can run the script fine, it starts up the server with no errors, so I'm assuming everything is configured properly.

So I guess what I mean to say, can someone tell me briefly how run levels work, what I would need to do to get an example program Foo to startup at boot, and automatically shutdown at power down.  If you can, try to relate it someone to FreeBSD as that is what I am familiar with.

I thank you in advance for any help regarding this matter.

---

### Post by jazzmuzik on 2006-04-27
I take that by "network installation" you mean there's no gui on this install? If there is a gui you can do, System, Administration, Services and click the apache web server. I'm not sure how to do it at the command line. I just came from Fedora about a month ago and am still learning.

---

### Post by kaptainlange on 2006-04-28
That is correct, this is a bare minimum for the most part server.

---

### Post by steve.horsley on 2006-04-28
Ubuntu defaults to runlevel 2. For services to start at boot therefore, you need to make an entry in /etc/rc2.d. 

Imagine there is a script in /etc/init.d called myserver, and that you can start it with **/etc/init.d/myserver start** (or stop). Now you are ready to start playing with the different runlevels. To have the server started when the machine enters runlevel 2, make a symbolic link in /etc/rc2.d to the init.d script. The link must start with "S" followed by two digits, and init will start them in order. Frexample, create a link with the command:

**ln -s /etc/init.d/myserver /etc/rc2.d/S85myserver**

Now when runlevel2 is entered at boot, init calls all the S scripts in order with a start argument, e.g. **/etc/rc2.d/S85myserver start**
You can also arrange for the server to be stopped as the computer leaves level2 with this command:

**ln -s /etc/init.d/myserver /etc/rc2.d/K15myserver**

Now **/etc/rc2.d/K15myserver stop ** will be called after any other K links numbered 00 to 14 in rc2.d. 

I suspect that if a service has S links in both the old and new runlevels, init will not stop and start the service, but leave it running. It will kill a service with an S (and K) in the old runlevel if there is no S link inthe new runlevel.

---

### Post by steve.horsley on 2006-04-28
P.S.

Here is a simple script that could be dropped in /etc/init.d that you can use as an example...

```

#! /bin/sh

NAME="My Server"
HOME="/usr/local/myserver"
PROGRAM="myserver.py"
LOGFILE="myserver.log"


case "$1" in
start)
    echo "Starting $NAME"
    cd $HOME
    nohup ./$PROGRAM >> $LOGFILE 2>&1 &
    ;;
stop)
    echo "Stopping $NAME"
    killall $PROGRAM
    ;;
restart)
    echo "Starting $NAME"
    $0 stop
    sleep 2
    echo "Starting $NAME"
    $0 start
    ;;
*)
    echo "Usage: $0 {start|stop|restart}" >&2
    exit 1
    ;;
esac
exit 0

```

Properly written servers have the ability to write their process id to a file that you can read to kill the server by process id, instead of having to use the rather dirty killall.

---

### Post by trent dillman on 2006-04-28
or, instead of killall you could use pidof...

---

### Post by kaptainlange on 2006-04-28
Thank you for that write up, that helped considerably.  The main confusion I was having was exactly where the script should reside, but that cleared it up.

Thank you for your replies!

---


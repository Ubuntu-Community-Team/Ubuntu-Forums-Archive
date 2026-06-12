---
title: "define Runlevels (esp. Hula)"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by gwfire on 2006-01-18
We're running the newest version of ubuntu.

after installing dhcp and dns manually, we installed the hula-project as a mailserver! so far everything is working fine! ubuntu works, the rest works, hula also works after entering the command-line. but we have the big problem, that we must enter these command-line everytime we restart the system. we know, that we must edit some files (runlevel files?!) so that hula or another apps will run during the system-start.

can anyone help??

Cheers GW

---

### Post by Stealth on 2006-01-18
Check this customization guide here: [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

They talk about runlevels, and a way to configure the processes for them :)

---

### Post by steve.horsley on 2006-01-18
I'll try and explain my understanding of runlevels. There are several runlevels that you can choose as the machine starts up, and each runlevel has a different selection of services running. 

In Red Hat based distros, runlevel 1 is single-user mode with only enough services running for the root user to use the machine. Runlevel 3 is all the basic services including network services, but no graphical X interface running. Runlevel 5 is all services including the GUI.

In Debian and Ubuntu, all runlevels are configured identically by the installer. For  Debian/Ubuntu, the default runlevel is level 2. For red hat, it is 3 or 5 depending on whether the computer is to start a GUI when it boots (generally not for servers).  The file /etc/inittab has a line that gives the default runlevel for startup.

You can switch between runlevels with for instance **sudo init 5** to enter runlevel 5. **init 0** and **init 6** cause a shutdown and a reboot respectively.

For the services that are started (or not) in the various runlevels, a script is placed in /etc/init.d that can start or stop the service. Below is a sample script from a file /etc/init.d/splashserver. It's pretty ugly in that it stops the service by killing the process, but it does the job. This can be called with start or stop arguments, e.g. **/etc/init.d/splashserver start**.

```
#! /bin/sh

NAME="Splash Server"
HOME="/usr/local/splash"
PROGRAM="splashserver.py"
LOGFILE="/var/log/splashserver.log"


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
    $0 stop
    sleep 2
    $0 start
  ;;
*)
  echo "Usage: $0 {start|stop|restart}" >&2
  exit 1
  ;;
esac
exit 0

```

For each runlevel there is a directory called /etc/rc0.d, /etc/rc1.d etc. These directories can contain symbolic links to the service start/stop scripts in /etc/init.d. To provide some control over the order in which services are started and stopped, these links are named starting with either S or K (Start/Kill) followed by a 2-digit number. So If I want my server to be started when runlevel 3 is entered, I create a symlink to /etc/init.d/splashserver from /etc/rc3.d/S90splashserver, which because of the high number means it will be one of the later services to be started. Similarly, I would create a link /etc/rc2.d/K10splashserver so that the system calls **/etc/init.d/splashserver stop** as it transitions from runlevel 3 to 2. 

I have found clear documantation in Solaris that states that a server booting to runlevel 3 will transition through all the startup links in level 0, then 1, then 2, then 3, and that on shutdown it will execute the klll links in 2, 1, 0. I have not seen difinitive documentation for Linux stating whether it visits all the imtermediate levels or not. I'd love to know for sure but haven't got round to testing. Also, for Solaris, you use **pkill** instead of **killall.** 

I rather like the program bum for managing these symlinks in a GUI. [https://wiki.ubuntu.com/BootServices](https://wiki.ubuntu.com/BootServices)

Hope this helps.

---


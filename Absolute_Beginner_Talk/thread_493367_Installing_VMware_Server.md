---
title: "Installing VMware Server"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-07-05
I had installed Ubuntu but I messed some things up trying to do a unichrome pro setup.  So, I borrowed a 6.10 CD from a friend and have installed it and have unichrome pro working now.  I want to put Windows in a virtual machine within Linux, so I downloaded VMware Server since it seems to be recommended the most.  The version was the newest (1.40??).  At any rate, I got an error in the configuration and VMware Server doesn't start.  If anyone could help me I would appreciate it:D  Below is the end of the setup when it was running the config routine:

The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

Unable to find any instance of the super-server "inetd" or "xinetd".  It is 
possible that you do not have one of these packages installed on this machine. 
Please install "inetd" or "xinetd".

If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run 
/usr/bin/vmware-config.pl after you fix the super-server.

Hit enter to continue. 

dave@dave-ubuntu:~/Desktop/vmware-server-distrib$ 



Thank you!;)

---

### Post by Raineer on 2007-07-05
xinetd is required for most remote connections. This is what you need to install and start, I *believe*
```
sudo /etc/init.d/xinetd start
``` will suffice to start it after it's installed, which is probably sudo apt-get install xinetd

---

### Post by anewguy on 2007-07-05
Thank you, Raineer!!  Works great!:D  Out of curiosity, if I am the only user on my computer, do you know why it needs this remote connection stuff, or is that just one of those things that comes with a true multi-user operating system?

Thanks again!:D:D

---

### Post by scxtt on 2007-07-05
it's just part of the standard server package - it's most likely needed for vmware-serverd to start up (maybe to even connect to localhost) ...

do an **sudo lsof | grep TCP** and you should see *:902

---


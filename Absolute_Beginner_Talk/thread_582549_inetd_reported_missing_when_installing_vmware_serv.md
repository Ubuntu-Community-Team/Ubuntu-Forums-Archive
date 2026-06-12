---
title: "inetd reported missing when installing vmware server"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by encryptkeeper on 2007-10-20
Hey everyone when I try to install VMWare server on 7.10, I get this message in the terminal:
Unable to find any instance of the super-server "inetd" or "xinetd".  It is 
possible that you do not have one of these packages installed on this machine. 
Please install "inetd" or "xinetd".

If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run 
/usr/bin/vmware-config.pl after you fix the super-server.

Can anyone tell me how to fix this?

---

### Post by R.Bucky on 2007-10-20
I never received those messages on my install, but my server STILL does not work. Pain in my ars. Waiting for a few days before trying again to avoid beating my mouse or keyboard. It will take a few weeks to get those bugs out. 

I have no input for you other than "keep on keep'n on."

---

### Post by bashir on 2007-10-20
I got the same message when trying to install vmware server 1.0.4

i tried doing an apt-get for xinetd and got the following :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xinetd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xinetd has no installation candidate

so i am waiting for a fix also ....

UPDATE: 
i checked my /etc/apt/sources.list file and it had most of the sources hashed out.
so i removed the # infront of all the ubuntu sources and ran  sudo aptitude install xinetd and xinetd installed.
now, time to re-install vmware (since i uninstalled it)

---

### Post by austinjh on 2007-10-21
I installed "xinetd" through synaptic and re-ran "sudo /usr/bin/vmware-config.pl" and everything installed perfectly.

I'm surprised that xinetd wasn't already installed but I'm guessing that this is something to do with changes under the hood in 7.10 gutsy. (somebody else may know why)

Running 7.10 Gutsy 64bit

---

### Post by kingtech on 2007-10-31
Also had this problem, went into synaptic, turned the cd rom off as a source in repositories, reloaded, then it would find xinetd and allow me to install it... ready to do vmware now!!:guitar:

---


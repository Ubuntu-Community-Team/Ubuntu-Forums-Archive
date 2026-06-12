---
title: "Hamachi auto start on login ??"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Straker on 2006-01-21
Hi.

I have successfully installed and am running Hamachi, however, can't seem to get it to start automatically upon login.  Yes, I have checked the hamachi forums, etc. to no avail.  

So, to cut to the chase:

hamachi needs "tuncfg" to be run before it can start, however, tuncfg can only be started by sudo, which requires user interaction (password).  So my question is (and this is not limited to this hamachi problem):

**How can one write a script or launch a process automatically upon system login/boot-up that requires a super user password and skip the user-interaction needed to finish that process successfully?  In other words, run a super-user or root process without having to enter the password?**

I know that was a mouthful but any help is much appreciated.

---

### Post by sidd-tx on 2006-07-25
Well, this is sorta what I was looking for. I also have installed Hamachi and got it running using this guide:

[http://www.ubuntuforums.org/showthread.php?t=135036](http://www.ubuntuforums.org/showthread.php?t=135036)

But after each boot, I have to issue this command:

sudo hamachi -c /etc/hamachi go-online network

to connect to the network I created. Straker,, you're telling me, that in all your searching, there is no way to get Ubuntu to automatically login to my network without my intervention?

I came across this script for Fedora Core to get it all working automatically. 

[http://forums.hamachi.cc/viewtopic.php?p=16726#16726](http://forums.hamachi.cc/viewtopic.php?p=16726#16726)

Does Ubuntu have chkconfig?



Sidd...

---

### Post by wyth on 2007-08-11
Was this ever figured out?  I'd like to do the same, but haven't found a good solution as of yet.

---

### Post by wyth on 2007-09-14
One method that works rather nicely if you're using a gui frontend (liike [gHamachi]("http://penguinbyte.com/") or [this new open source one that is yet nameless]("https://forums.hamachi.cc/viewtopic.php?t=15682&highlight=gui")):

You can chown /sbin/tuncfg, then add that to the Start Up in System - Preferences - Sessions. When you start the frontend, everything pops right up without any of that logging in stuff.  

I tried adding gHamachi to the start up along with tuncfg, but gHamachi was called before tuncfg was loaded, and it failed.  There's probably [a way around this through using the /etc/rc.local file]("http://ubuntuforums.org/showthread.php?t=549172&highlight=tuncfg"), but I haven't bothered with it.

Edit: This *was* working for me, but now tuncfg is asking for the password, even though I own it and set it to execute on start.  

However, [this page]("http://www.neohide.com/automatic-start-up-hamachi-for-ubuntu-feisty-fawn") had some directions that did work.  To wit:

[LIST=1]
[*]Create the start-up script for hamachi, as shown below. Remember to change the user name "your name" *(line 5)* to your system user name in Ubuntu (or your Linux distribution).
[INDENT] #!/bin/bash
###################################
### Start-up script for Hamachi ###
###################################
USER=your name
case "$1" in
start)
    /sbin/tuncfg
    /bin/su - $USER -c "hamachi start"
    ;;
stop)
    /bin/su - $USER -c "hamachi stop"
    ;;
restart|force-reload)
    /bin/su - $USER -c "hamachi start"
    /bin/su - $USER -c "hamachi stop"
    ;;
*)
    exit 1
    ;;
esac
 exit 0 
[/INDENT]
[*]Make the script executable:
[INDENT]chmod +x hamachi
[/INDENT]
[*]Move the script to /etc/init.d/ directory:
[INDENT]sudo mv hamachi /etc/init.d
[/INDENT]
[*]Finally, link the script to the appropriate run-level for booting up the system:
[INDENT]sudo ln -s /etc/init.d/hamachi /etc/rc2.d/S99hamachi
[/INDENT] [INDENT]sudo ln -s /etc/init.d/hamachi /etc/rc2.d/K99hamachi
[/INDENT] It seems **2** is the default level for Debian and Ubuntu. In most other distribution, it is **5**. 
[*]Finally, reboot your system and Hamachi will be automatically loaded and connected to the server.[/LIST]

---

### Post by CaptainInsaneO on 2007-09-14
I'd like to help you with this problem, I'll start working on it this weekend.

Edit: You could try this nice howto: [http://forums.hamachi.cc/viewtopic.php?t=3421](http://forums.hamachi.cc/viewtopic.php?t=3421)

let me know if it works for you, if it doesn't I'll still work on it. If it does, I won't bother. :)

Good luck!

---


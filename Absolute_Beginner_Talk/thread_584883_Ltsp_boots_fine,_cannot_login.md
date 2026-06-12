---
title: "Ltsp boots fine, cannot login"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Azrayal on 2007-10-21
Hi, 

I've just setup a new 7.10 ltsp server, but for the life of me I cant figure this one out. 

The terminal boots fine from my thin client and goes to the gui login prompt, I type in my username and password and it seems like its about to login but instead just drops back to the gui login prompt once again.. anyone any suggestions?

It seems to be some sort of sessions issue as the username and password I'm using are correct, even confirmed that in the logs.

Sorry I've posted this in the wrong place.. please delete*

---

### Post by SpiritIsReality on 2007-11-08
howdy
I had the same login trouble but I got an error message of 
> 
This workstation isn't authorized to connect to server error message on client, please run commands sudo ltsp-update-sshkeys and sudo ltsp-update-image (in this order) reference: [WWW] [https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296) 
from here [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)
Do you think it could be it?
trailshttp://ubuntuforums.org/showthread.php?t=599166
With a Ubuntu Desktop 7.10 LTSP server,    [http://ubuntuforums.org/showthread.php?t=599166](http://ubuntuforums.org/showthread.php?t=599166)                                          when logging in from a client, if I type in the wrong password 3 tries, the screen blacks out and comes back to a fresh login window. I'm just saying that I'd guess it's not the error message problem I quoted.

---

### Post by ahmadzainul on 2008-05-05
here is have the same problem

---

### Post by joehill on 2008-05-08
I have the same problem.  It's not the same as when you get the message "this client is not authorized to connect" etc.  That can be fixed by typing "sudo ltsp-update-sshkeys".

Any ideas?  Same thing happens to me--the screen goes black for a while then falls back to the ldm screen.  I try on tty1 and it says my password is incorrect.  I've occasionally been able to log in, but I haven't figured out what I'm doing differently.

---

### Post by joehill on 2008-05-08
It's working now.  I'm not sure which of these things did it, but I copied these lines (increasing color depth) from the edubuntu help site into my /var/lib/tftpboot/ltsp/i386/lts.conf:

X_COLOR_DEPTH=24
LOCALDEV=True
SOUND=True
NBD_SWAP=True
SYSLOG_HOST=server
XKBLAYOUT=en

I don't know ltsp enough to see how any of these would affect it, but hopefully this will help someone else who had the same problem with the default settings I had.

---


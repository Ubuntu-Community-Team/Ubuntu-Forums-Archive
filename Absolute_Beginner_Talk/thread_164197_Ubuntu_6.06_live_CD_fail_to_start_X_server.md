---
title: "Ubuntu 6.06 live CD: fail to start X server"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by tuga on 2006-04-22
I am trying to install the ubuntu 6.06 (AMD64) from the live CD, but when ubuntu is starting from the live CD the Xserver fails.
I had this problem (xserver fail) with ubuntu 5.10 and the solution was to install the ubuntu 5.10 and then run "sudo dpkg-reconfigure xserver-xorg" -> choose vesa. The graphic card is a ATI X800GTO.

Ubuntu 6.06 is installed with espresso but espresso requires the GUI. So, I can not start the GUI to proceed with the installation.

Is there a way to overcome this situation?

Thanks in advance.

---

### Post by taurus on 2006-04-22
You can try installing Dapper beta using the server mode at the prompt.  Then, install Gnome and configure your X after that with
```

sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Mustard on 2006-04-22
Sounds like a good plan to me. :)

---

### Post by tuga on 2006-04-22
I boot the PC from the 6.06 live CD, choose "start ubuntu" and after a while got the message that the xserver failed.
Then tried "sudo apt-get install ubuntu-desktop" and get the message:
"Reading package lists... Done
Building dependency tree... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

After run "sudo dpkg-reconfigure xserver-xorg" to configure the X, how do I start the GUI?

Sorry, but I am new on this...

---

### Post by moffa on 2006-04-22
I think its "startx"

---

### Post by Mustard on 2006-04-22
Either startx or sudo /etc/init.d/gdm restart

---

### Post by tuga on 2006-04-23
With "startx" the screen gets black and the only solution is reset the PC.
"sudo /etc/init.d/gdm restart" also fails:
starting gnome display manager... FAIL.

---

### Post by Mustard on 2006-04-23
[QUOTE=tuga]With "startx" the screen gets black and the only solution is reset the PC.
"sudo /etc/init.d/gdm restart" also fails:
starting gnome display manager... FAIL.[/QUOTE]

So that was using 'vesa' drivers?  What resolutions were you going for?

---

### Post by tuga on 2006-04-23
Yes this is after boot from the live cd, run "sudo dpkg-reconfigure xserver-xorg" choose vesa and choose the resolution 1024x768.

---

### Post by htinn on 2006-04-23
You may need to do that a little differently:

[https://wiki.ubuntu.com/FixVideoResolutionHowto#head-42bafbcee7a10ed50f2d9016555557b9874be252](https://wiki.ubuntu.com/FixVideoResolutionHowto#head-42bafbcee7a10ed50f2d9016555557b9874be252)

---

### Post by tuga on 2006-04-23
When I try "sudo aticonfig" from the command line the reply is "command not found".
Please notice that I am trying to install ubuntu 6.06 from the live CD.

I have the ubuntu 5.10 installed but when trying to update with the "gksudo "update-manager -d"" the reply is that the system is up-to-date.

---

### Post by H3HI on 2006-08-28
> **htinn said:**
> You may need to do that a little differently:

[https://wiki.ubuntu.com/FixVideoResolutionHowto#head-42bafbcee7a10ed50f2d9016555557b9874be252](https://wiki.ubuntu.com/FixVideoResolutionHowto#head-42bafbcee7a10ed50f2d9016555557b9874be252)


i do all the steps follow this article.
when use startx for restart the installation,
the system said:

> xauth:  creating new authority file /root/.serverauth.5056

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux zaphod 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 23 21:13:19 2006
(==) Using config file: "/etc/X11/xorg.conf"

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.


of course, this is my first time install ubuntu from the live cd 6.06, not update the x server.

---

### Post by TFX360 on 2006-08-28
I've got the exact same problem with my ATI X800XT. BUT only with the AMD64 version of Ubuntu 6.06. Don't know if it helps thought I just mention it... Posted my problem in the 64bit forumpart, no replies though...

By the way on my x86 install the non-grapical screen (ctrl+alt+F1) flickers every 10 to 20 seconds. On, off, on, off, on, off, on, off, on.


Kind regards,


TFX

---


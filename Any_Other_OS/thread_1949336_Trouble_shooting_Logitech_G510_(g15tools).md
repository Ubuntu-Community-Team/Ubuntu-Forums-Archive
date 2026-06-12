---
title: "Trouble shooting Logitech G510 (g15tools)"
date: 2012-03-29
forum: Any Other OS
---

### Post by jcllings on 2012-03-29
I know there are other threads regarding this topic but most of em have been dead for a year. Note, while I would love to get some help, it may be that this thread winds up being a published commentary about what I did to solve the issues involved... but again I sure could use some help and/or advice. ;-) It may be useful to somebody anyway.  

*My Hardware*

This box is actually a Linux Mint box (wheezy/sid). Wound up on Mint when I had some trouble with the last version of UI graphics. Had to keep trying Linux distros till I found one that had what I needed.

jim@midknight:~/g15tools-source/g15tools/trunk/g15daemon$ uname -a
Linux midknight 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

*Relevant Links*

The site where these tools are actually produced is here:
[http://www.g15tools.com/](http://www.g15tools.com/)

Here are some resources for reference:
[https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)

OK, here we go. I&#7743; pretty inexperienced with trouble shooting keyboards but not troubleshooting, per se. OK, so it&#347; a USB Logitech G510. I get post install errors:

...
Setting up libg15render1 (1.3.0~svn316-2.2) ...
Setting up g15daemon (1.9.5.3-8.2ubuntu1) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

uinput turns out to be a required kernel module and worse, it doesn´t appear to be available by default:

jim@midknight:~$ sudo lsmod | grep uinput
jim@midknight:~$ sudo modprobe uinput
jim@midknight:~$ sudo lsmod | grep uinput

Nothing? Hmm.... OK according to the thread below, it ISN´T a module any more as it is now built directly into the kernel due to a bluetooth support issue periphery to our keyboard issue. See below:

[http://tech.shantanugoel.com/2011/02/22/ubuntu-maverick-uinput-problem-solved.html](http://tech.shantanugoel.com/2011/02/22/ubuntu-maverick-uinput-problem-solved.html)

Having read the above, the work around might be: 
sudo chmod go+rwx /dev/uinput
sudo ln -s /dev/input/uinput /dev/input/uinput

...except we still get the post install error. Maybe this is why:

jim@midknight:~$ ls /dev/input/uinput 
ls: cannot access /dev/input/uinput: Too many levels of symbolic links

Seems like there might be a circular link in there somewhere. Anybody know how to deal with this?  Hmm... I might be able to build the code from source now that I know. I could search the source for ¨/dev/input/uinput¨ and remove the input dir. 

Of course, the biggest problem I have with this keyboard is just getting the keys to punch out the right characters. I note for example, that I have to hit the quote key twice to get any kind of quote character. ¨ <- Some of these characters don´ look right. Since I&#7743; having difficulty with my passwords, I am assuming these are literally the wrong characters. Also, I&#7743; not convinced that there isn´t a character set associated with the keyboard that I need to change. Would like to see a work-around for people who just want to type on the doggone thing. 

I was unable to determine from lsusb output which device was the Logitech G510 I am using so I dumped lsusb to files with (plugged in) and without (not plugged in) and then did a diff. Result was:

jim@midknight:~$ diff with without 
14d13
< Bus 002 Device 017: ID 046d:c22d Logitech, Inc. 

...so the above has to be the keyboard I guess, but it sure seems odd. I saw in another thread that there might be a typo somewhere wherein this might be relevant.  Will have to watch out for that.  

More on this latter...

---

### Post by Perfect Storm on 2012-03-30
Moved to Other OS/Distro Talk.

---


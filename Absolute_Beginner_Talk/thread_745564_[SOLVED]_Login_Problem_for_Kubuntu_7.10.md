---
title: "[SOLVED] Login Problem for Kubuntu 7.10"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by ritdude on 2008-04-04
I recently tried to connect to a wireless connection in school my manually configuring it.  Didn't work (but this isnt the question, just back ground.)    After that I restarted the computer and now I am having trouble logging in.  Whenever I log into my account (admin account), the screen goes to the logging in splash screen, then goes blank (with a cursor); the KDE is missing.  I tried to login in using failsafe mode a noticed the prompt was different.  The prompt is now:  greg@SCCC-Public:/$  where SCCC-Public was the name of the network i tried to log into before this problem.  Is there a way to change the prompt back to greg@[my_computer_name]: so that KDE will work again?

---

### Post by Rocket2DMn on 2008-04-04
You can try reconfiguring X back to its initial settings by running
```
dpkg-reconfigure xserver-xorg -phigh
``` from the recovery kernel (the second option at the GRUB menu).  Then
```
reboot
``` and boot into the regular kernel.
Otherwise you can manually reconfigure X with this guide - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by ritdude on 2008-04-05
I don't believe this to be an xorg.conf problem. I spent the last day messing around with it, but thanks for giving it a shot.  The kdm is running and the splash screen after logging in works (it just always stops finishing).  I am stuck with just my back ground and now kde.  I think the porblem is a network one, it seems to be trying to use a network name in my command line prompt (my prompt is as follows: gregory@SCCC-public:~$ ) where SCCC-public is the name of a wireless network i recently logged into.  I really dont know the technical terms, so this post might be confusing, but if anyone has any ideas, i'd appricate it

---

### Post by ritdude on 2008-04-12
the problem was a hostname related problem

SCCC-Public has a hyphen in it, which I was told can screw things up; all I needed to do was change the "/etc/hostname"  file to a name without special chars to fix it.  Thanks for your help.

---


---
title: "help with synaptic package manager"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by bbrobb on 2007-04-15
Wow, I'm new to linux, this is the first problem I have been unable to solve.  While using synaptic package manager to download the flashplugin progress on the download stopped and the program stopped responding, I rebooted and attempted to start synaptic again.  Error message E: dpkg , must run dpkg --configure -a manually  , or something to this effect.  After reading up on the subject a bit I ran what you see below in the terminal...

b@b-desktop:~$ sudo dpkg --configure -a
Password:
Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading... 

nothing, just a flashing cursor after downloading and terminal commands like 'exit' are not responded to.....

now when I try to open synaptic I get this message....

Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

please help!

---

### Post by lamalex on 2007-04-15
do a ps -A an look for any apt processes and kill them, then try again.

---

### Post by speeves on 2007-04-15
The flashplugin-nonfree package simply downloads the flash tarball from:
[http://macromedia.mplug.org/](http://macromedia.mplug.org/)

I would bypass this, but downloading the tarball yourself and installing it with these instructions:
[http://technowizah.com/2006/10/debian-how-to-flash-9.html](http://technowizah.com/2006/10/debian-how-to-flash-9.html)

Remember, Ubuntu is a Debian derivative, so these instructions should work well for you :)

Here are more instructions from the Debian wiki:
[http://wiki.debian.org/FlashPlayer](http://wiki.debian.org/FlashPlayer)

Plus, Ubuntu specific instructions:
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by bbrobb on 2007-04-16
Thank you very much for the help.  I can now load synaptic but still unable to run it, the error message is: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

looks like I'm back where I started.  
once I can get synaptic repaired then I can move forward and try the method that speeves suggests, till then how do I get access to the repositories and synaptic back???
Thanks and I promise that I will help others once I become more proficient!  

kind regards, 
Brett

---

### Post by lamalex on 2007-04-16
did you try running dpkg --configure -a?

---

### Post by bbrobb on 2007-04-16
yes, I did that and it says:

Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading...

and seems to just hang there, I'm doing it again right now, just the flashing cursor.  Thanks for your help!

---

### Post by bbrobb on 2007-04-16
... hope the thanks for you help didn't sound sarcastic, I really do mean it, although yes I'm still stuck...

---

### Post by bbrobb on 2007-04-16
... hope the thanks for your help didn't sound sarcastic, I really do mean it, although yes I'm still stuck...

---

### Post by bbrobb on 2007-04-16
Thanks lamalex and speeves, I've got it sorted now.  I used the commands from technowizah.com to download and install from a terminal session, great learning experience!  Anyway this seems to have unlocked synaptic, that was scary but I'm better now.  

cheers!

---


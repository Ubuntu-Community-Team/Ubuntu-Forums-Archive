---
title: "Super User password?"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by janhelge on 2005-11-24
When Ubuntu 5.10 was installed there was no question about su password... In ubuntu 5.04 you had a root-treminal. I need to set the su password. Any suggestions??

---

### Post by wishyjr on 2005-11-24
i think it should be the same as your user password.

---

### Post by frodon on 2005-11-24
Endeed, after a fresh install your root password should be your user password.
To become root in a terminal use the "sudo su" command.

---

### Post by linbetwin on 2005-11-24
root password is disabled by default in Ubuntu.
See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Use **sudo **instead of **su** and type your user password.

---

### Post by tonym on 2005-11-24
Try to avoid this if you can.  Ubuntu is based on root not baing accessible directly.  Instead you use the sudo command to do anything requiring root priviliges.

If you do want to set the password use

sudo passwd

First you have to enter your non-root password then the new root password.

Regards

Tony

---

### Post by patrick295767 on 2005-11-24
[QUOTE=janhelge]When Ubuntu 5.10 was installed there was no question about su password... In ubuntu 5.04 you had a root-treminal. I need to set the su password. Any suggestions??[/QUOTE]
  
The normal installation: 
u do sudo su
from the user (at installation)
then, passwd 
enter the root password
and that's it !
  
If you mess up, take knoppix cd, and have a look there:
[http://www.ubuntuforums.org/showthread.php?t=64557&page=6](http://www.ubuntuforums.org/showthread.php?t=64557&page=6)
to get the passwrd

---

### Post by somody on 2005-11-24
To stop having to type "sudo" before everything, you can type "sudo bash" then it's basically the same as "su" but it only lasts the session in the terminal ;).

---

### Post by fopetesl on 2005-11-24
Hey, newbie Breezy user here.
User password works OK for "root" level in VC7 but it doesn't work in (say) in VC1.
Is there NO login as root in VC1..3 ??
I do not want to have to 'sudo' EVERY command.



BTW, I  ditched SUSE 10 because it couldn't load GRUB correctly AND I could not set my laptop screen res correctly.  I also ditched SARGE since it only had kernel 2.4.x - no hotplug (updating kernel? No bl**dy way!)

---

### Post by somody on 2005-11-24
1) Look at my post (1 above yours)
2) Sudo "gdmsetup" without the quotes and goto the security tab.  Check "allow root login" or "Allow root access as Root" or something like that.  That will let you LOG IN as root but WARNING!  no restrictions, and it's not like windows....:)

Also, the kernel update takes about 5 minutes :p

---

### Post by fopetesl on 2005-11-25
somody (nearly misspelet!) TY.
However, I cannot run "sudo gdmsetup" in VC1 because:
   [COLOR="Red"](gdmsetup:8840) Gtk-WARNING **: Cannot open display[/COLOR]
which makes sense because not in VC7.
VC7 does not have a terminal window (unless I install?) so any other suggestion, please?

---

### Post by somody on 2005-11-25
I'm a newbie as well, so I have no idea...sorry!

---

### Post by fopetesl on 2005-11-25
OK. The answer which worked for me:
install "nautilus-open-terminal" using synaptic. (need to turn on universe)
For some reason need to reboot before it activates.
Right-click on desktop and open a terminal.
type "sudo gdmsetup"
Password is current user password.
Enable the "allow root user"(?) option in security.
exit gdmsetup. [COLOR="Blue"][thanks somody][/COLOR]
Then (at any terminal screen VC1..7) type:
sudo passwd root
(your logins [COLOR="Red"]password[/COLOR])
(root [COLOR="Red"]password[/COLOR])
(retype [COLOR="Red"]root password[/COLOR])
see: [http://ubuntuforums.org/showthread.php?t=94957&highlight=root+password](http://ubuntuforums.org/showthread.php?t=94957&highlight=root+password)

Enjoy:smile: !

---


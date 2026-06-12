---
title: "Ubuntu Crash - Help"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by colemanc on 2006-05-17
Hi, New Ubuntu / Linux user for about 4 months. Have totally loved Ubuntu and have no plans to ever go back to Win.Strangest thing happened to me when I arrived in the office.

Left my desktop on overnight. It was attached to the net via cable modem; ubuntu 5.10 running.

Sat in front of my computer this morning, logged in and attempted to start firefox. Message said that it was not responding. Being from windows, i immediatly respond by initiating a restart.

When the restart begins, it does not restart Ubuntu. Instead it is asking if I want "to use a graphical installer, if so hit enter". Confused, I hit enter, and a message tells me that it is in the process of Installing Fedora???? What the %*#!?.

I assume I was the victim of some sort of malicious attack overnight. I power down and I then insert the Ubuntu install CD and proceed to do an re-install. The Ubuntu Install CD works fine and reaches the point where it reqiures the CD to be removed and then to a reboot to continue the install. At the reboot, it again is prompting me to install Fedora and actually begins installing Fedora Core!

Any ideas on what happened and how do I get Ubuntu to install and then SECURE it to prevent this from happening again, assuming this was a malicious act. Any help would be greatly appreciated.

---

### Post by Caligula on 2006-05-17
this is weird...
are you sure you didn't just leave a fedora CD in the other cd drive?

---

### Post by Sef on 2006-05-17
> ...then SECURE it to prevent this from happening again, assuming this was a malicious act.

Did you have a firewall installed?

If not, then 

sudo apt-get update

sudo apt-get install firestarter

or look for it in Synaptic (System > Administration > Synaptic Package Manager)

---

### Post by Nano Geek on 2006-05-17
Your positive that you don't have a Fedora disk in one of your dirves?

---

### Post by colemanc on 2006-05-17
No fedora cd in any of the drives. Fedora 3 was installed previous, but during the Ubuntu install I directed that the disk be erased. 

No i did not have a firewall installed, and this is why I am suspecting a malicious attack of some sort. If I ever get umbutu working again, the first thing i will do is install a firewall

---

### Post by colemanc on 2006-05-17
Ok guys, thanks for your quick responses. You were right. I added a dvd drive yesterday and low and behold there was a fedora cd in it. ](*,) Thanks again

---

### Post by glotz on 2006-05-17
:)

Now, to calm your nerves, proceed to [http://www.bastille-linux.org/](http://www.bastille-linux.org/)
And then read [Gain root without root password (locally)](http://www.ubuntuforums.org/showthread.php?t=177984)

---

### Post by colemanc on 2006-05-17
Thanks, this would have helped me out earlier. But I learned something today besides the fact that Im an A@&H*%#. :)

---

### Post by bluenova on 2006-05-17
Roflmao :D

---

### Post by Caligula on 2006-05-17
LOL:-D 
this was a good one...
:D :D :-D

---


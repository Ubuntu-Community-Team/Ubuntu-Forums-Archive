---
title: "Running Ubuntu an Win XP"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by jabbapam on 2008-01-08
I was looking at this site where it shows a video of someone running feisty and XP together in a box or cube.

[http://www.youtube.com/watch?v=j0mNWQTw0nc&eurl=http://www.ubuntuvideo.com/node?page=8]("http://www.youtube.com/watch?v=j0mNWQTw0nc&eurl=http://www.ubuntuvideo.com/node?page=8")

Is this easy to do?

I have programs in windows that I need to use as well as in feisty 7.04 on a asus L4500r and I'm always restarting into both when I need to run different programs.

---

### Post by bodhi.zazen on 2008-01-08
You need to look at Virtualilzation. Something like VMWare or Virtual box. Additional options include QEMU.

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by Pevichaey5 on 2008-01-08
i was looking into this kind of thing the other day and i can confirm it is fairly simple to set up

just search for 'virtual box' in the synaptic package manager and install it.  i'm not sure how to add myself to the vbox~~~ group yet, so i jus run it in root, not recomended, but it works

---

### Post by loudnlownoma on 2008-01-08
> **thexero said:**
> i was looking into this kind of thing the other day and i can confirm it is fairly simple to set up

just search for 'virtual box' in the synaptic package manager and install it.  i'm not sure how to add myself to the vbox~~~ group yet, so i jus run it in root, not recomended, but it works

There should be an option under System > Admin > Users and Groups.  Hit the Manage Groups tab, find the vbox groub and add your login to it, reboot.  Should work like a charm.  :)

---

### Post by bodhi.zazen on 2008-01-08
> **loudnlownoma said:**
> There should be an option under System > Admin > Users and Groups.  Hit the Manage Groups tab, find the vbox groub and add your login to it, reboot.  Should work like a charm.  :)

"Reboot" is soooo Windows :lolflag:

All you need to do is log out and back in. In Linux Rebooting is (usually) only required if you want to change kernels or hardware.

---

### Post by loudnlownoma on 2008-01-08
> **bodhi.zazen said:**
> "Reboot" is soooo Windows :lolflag:

All you need to do is log out and back in. In Linux Rebooting is (usually) only required if you want to change kernels or hardware.

I was thinking the same, but for some reason the user groups didn't seem to update right.  Although I may have just tried restarting X (Ctrl-Alt-Backspace) rather than actually choosing Logout and logging back in.  Would there be a difference between those two?

---

### Post by bodhi.zazen on 2008-01-08
Ctrl-Alt-Backspace kills X -> GDM restarts (GDM is still running even after you have logged in).

Logout and back in allows programs and your desktop to close gracefully.

In reality, not much difference.

---

### Post by jabbapam on 2008-01-08
Two things have gone wrong so far.

I'm following this quide
[URL="http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu"]

1- When i go to 'Select physical disk' page of VMware setup

I get = Failed to load partitions for device /dev/hda: Permission denied

2- From a suggestion on this thread=

> **loudnlownoma said:**
> There should be an option under System > Admin > Users and Groups.  Hit the Manage Groups tab, find the vbox groub and add your login to it, reboot.  Should work like a charm.  :)

I cant find vbox groub in Users and Groups.

---

### Post by bodhi.zazen on 2008-01-09
Well, the vboxusers group is used by virtualbox and does not apply to VMWare

Second, booting a physical hard drive can be difficult. The default behavior is to boot a virtual machine and re-install an OS.

Third, you may need to run VMWare as root <shudder>

---

### Post by shareMenaPeace on 2008-01-09
Here is a guide i used to install virtualbox ...
[http://n00buntu.blogspot.com/2007/11/tutorial-ubuntu-compiz-virtualboxmagic.html](http://n00buntu.blogspot.com/2007/11/tutorial-ubuntu-compiz-virtualboxmagic.html)

---

### Post by jabbapam on 2008-01-09
I don't think my laptop will cope with virtual box so wont try that... at the moment anyway.

Everything is pretty good with the vmware setup although to get around the permission thing I had to install via the command line.

Is there a short cut that I can make so it's a little more easy?

The other thing is I don't seem to have usb support, any suggestion would be great full.

---

### Post by loudnlownoma on 2008-01-10
I just got my USB working in Virtualbox the other day, VMWare I'm not so sure though.  I know it worked out of the box in the Windows version I had, but not sure in Linux

---

### Post by bodhi.zazen on 2008-01-10
FYI : If you can run VMWare you can run Virtual Box :)

---

### Post by loudnlownoma on 2008-01-10
> **bodhi.zazen said:**
> FYI : If you can run VMWare you can run Virtual Box :)

That's what I was thinking.  I'm verry happy with Virtualbox, and it seems pretty light, runs great, and have had a much easier time with it than VMWare in Windows.    :)

---

### Post by gpilkay on 2008-01-18
I'm another vote for VirtualBox.  It's free, and overcame my trouble with Gutsy on my laptop (didn't want to partition, but Wubi didn't quite hack it for me).  Only troubles are USB (working on it) and screen resolution, though I rarely want to run full-screen Gutsey off my laptop anyway.  At home I have two hard drives.  At college, I tend to use Gutsey for more specialized functions.

---


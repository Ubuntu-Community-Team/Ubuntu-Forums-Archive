---
title: "Will Paypal $ To Whoever Can Fix My Problem"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by lookmomimonlinux on 2008-02-17
I only want to be able to add & delete files to my ipod using gtkpod, exhaile, or any program that is easy to use. If i have to give my first born to enable me to do this then so be it.

---

### Post by Origin415 on 2008-02-17
What sort of iPod is it? the newer ones have encryption that will make it more difficult -- I think Amarok might still be able to do it though. Otherwise, you should be able to plug it in and Gnome can mount it as a hard drive.

What errors have you had in trying so far?

---

### Post by articwolf939 on 2008-02-17
try a program call amarok is syncs to ipod very easliy should just be plug and go

sudo apt-get install amarok

or use synaptic

edit

and if ur music is on the ubuntu hd partition it should automatically find it and when u plg u ipod in it should auto sync

---

### Post by JoshuaRL on 2008-02-17
And we're happy to help, no money needed.  If you really want to give some, please donate it to Canonical, the makers of Ubuntu.  We try to go by the motto "You received free, give free."

---

### Post by lookmomimonlinux on 2008-02-17
I believe it is a 5th gen, 30 gb, model #A1136, with a date of 2005. Are you on AIM?

---

### Post by JoshuaRL on 2008-02-17
Also, you should have probably stayed with the original thread.

[http://ubuntuforums.org/showthread.php?t=699813](http://ubuntuforums.org/showthread.php?t=699813)

---

### Post by tdrusk on 2008-02-17
use banshee.

open a terminal and put 
```
sudo apt-get install banshee

```

that should do the trick :)

---

### Post by lookmomimonlinux on 2008-02-17
Alright, I dled Amarok and it's telling me to enter a pre and post command to configure the ipod with Amarok. Does anyone know these two commands?

---

### Post by harold4 on 2008-02-17
[Check this]("https://help.ubuntu.com/community/PortableDevices/iPhone") out.  The top two setup sections should help you out.

pre-command = mount the ipod
post-command = unmount the ipod

---

### Post by lookmomimonlinux on 2008-02-17
That did not work, i got: Media Device: No mounted iPod found

---

### Post by tdrusk on 2008-02-17
go to settings>configure amarok>media devices and add the ipod.

---

### Post by lookmomimonlinux on 2008-02-17
Any other way to mount this? or any other program that will recognize this? so far I've been unable to get exhaile, gtkpod and amarok to work with the help provided, not to sound ungrateful, but is there possibly any additional information not suggested that may be of help?

---

### Post by tdrusk on 2008-02-17
Banshee handles the ipod seamlessly.

You can install it by running
sudo apt-get install banshee 
in the terminal.

---

### Post by Origin415 on 2008-02-17
Go to System -> Preferences -> Removable Drives and Media and make sure that the "Mount removable drives when hot-plugged" and "Mount removable media when inserted" fields are checked on the Storage tab.

If they are and it still won't mount when plugged in (ie, an icon doesnt appear on your desktop), then post the output of

```
ls /dev
```
both when the ipod is plugged in and not plugged in.

---

### Post by JoshuaRL on 2008-02-17
Do you have either a Windows PC or a friend that has one with iTunes loaded?  I would suggest you go there and format it for Windows for sure.  I am starting to think that is your problem.

If Exaile, amaroK, and gtkpod don't work i sincerely doubt Banshee will.

---

### Post by lookmomimonlinux on 2008-02-17
> **tdrusk said:**
> go to settings>configure amarok>media devices and add the ipod.

I completed that step already and at the top left bar it says that it is mounted at/media/victor's ipod

but when i hit connect it says that it is not mounted?

---

### Post by tdrusk on 2008-02-17
> **lookmomimonlinux said:**
> I completed that step already and at the top left bar it says that it is mounted at/media/victor's ipod

but when i hit connect it says that it is not mounted?
just try using banshee.

It's a lot easier.

---


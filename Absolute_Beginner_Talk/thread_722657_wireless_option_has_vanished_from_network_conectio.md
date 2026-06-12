---
title: "wireless option has vanished from network conection"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by cragger on 2008-03-12
..it happened while i was trying to get ndiswrapper to work.. anyone know of a way to fix this?

---

### Post by neurostu on 2008-03-12
We are going to need more information.

What have you tried with NDISWrapper?

What wireless adapter do you have?

---

### Post by cragger on 2008-03-12
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-b0e306f00ab3b4adea24f483a5dd5bf05fbdaf08]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-b0e306f00ab3b4adea24f483a5dd5bf05fbdaf08")I used this guide to try to get it to work, and im pretty sure it works now its just theres no way to conect to wireless because i cant see it
wierless adapter?

---

### Post by cragger on 2008-03-14
so to make it more clear notice that the wireless option does not show up. it was there before but it has vanished after reboot, does anyone know of any way to fix this, or a link to a thread where someone has already covered this ? ive looked but i could no find any.
[IMG]http://i263.photobucket.com/albums/ii121/cragger_bucket/Screenshot-NetworkSettings-1.png[/IMG]

---

### Post by scottro on 2008-03-14
This means that the system doesn't see your wireless card.  
Perhaps you blacklisted something that was necessary for the system to see it and the ndiswrapper wasn't successful.  
(That's just a guess though.) 

At any rate, if the wireless option isn't appearing, it means that the system doesn't know there's a wireless device there.

---

### Post by MadMedis on 2008-03-14
If you had it working and it stopped working after you reboot, you may just need to reload the ndiswrapper module into the kernel.  Run:

sudo modprobe ndiswrapper

It may take about 10 seconds but that should fix it.  If there is any output to that command, please post it (there isn't any output when I run it).  If that doesn't fix it, make sure you have the correct drivers installed into ndiswrapper.  Run:

sudo ndiswrapper -l

That should produce something like this:

net8187b : driver installed
        device (0BDA:8189) present

If it doesn't, please post the results of that command.

---

### Post by cragger on 2008-03-14
scottro, i think your right, i remember doing something about blacklisting... so how do i fix that

and madmedis, i tried both thing and nothing happened and there was no output, so it is still not showing up.

---

### Post by cragger on 2008-03-16
can anyone help me??

---

### Post by MadMedis on 2008-03-19
After running "sudo modprobe ndiswrapper", run "sudo lsmod" and see if ndiswrapper shows up on that list.  Let us know one way or the other.  I believe that that should indicate whether ndiswrapper has been blacklisted or not.

Also, are you sure you followed the driver installation process correctly?  It's not a bad idea to go to the ndiswrapper's instruction manual (located here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/) scroll down to the section on "Install Windows Driver") and make sure you didn't miss anything.

---


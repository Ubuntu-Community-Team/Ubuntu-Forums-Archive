---
title: "Successful Partition Edit on G4 Mini"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by dank28 on 2009-01-22
I'm very new to ubuntu (and linux in general) but it's been pretty easy to find info all over about how to go about resize your windoze partition to enable a dual boot.  It's harder to find this info for macs, especially the PPC versions.  Some say it cannot be done, other say only on intel macs running 10.5.

Well after reading some at the following pages, I decided to give it a try.

[http://en.opensuse.org/Talk:PPC_Partitioning]("http://en.opensuse.org/Talk:PPC_Partitioning")

[http://www.macosxhints.com/article.php?story=20080216071647156]("http://www.macosxhints.com/article.php?story=20080216071647156")

AFTER I created and tested a clone of my current OS onto a firewire drive, I popped in the Hardy live cd, booted up and used gparted to shrink my OS X partition from 70 gb down to 55 gb, to make room for my install.  (Note that you have to use the editor from the System > Admin menu, as the resize is not an option during the install dialogues.)

It took about 3 hours to do this on my G4 1.5Ghz mini.  When it was done I shut down, and booted back up into OS 10.4 with no problems what-so-ever!  :D

AGAIN - PLEASE BACK UP ANY DATA BEFORE MESSING WITH YOUR PARTITIONS!!

I just wanted to post this as an FYI for any other PPC 10.4 users out there - You CAN edit your partition to make room for a dual boot.

** I haven't actually installed Hardy yet because for some reason it doesn't like to display anything thru my KVM switch.  (I had to connect direct to run my test last night.)  It works fine when I'm in the Mac OS, and also fine from a frakenstein PC box running Hardy, which I'm typing on now, but no go when trying the live disk.  This weekend I'll complete the install and let everyone know how things went.

Cheers, Dan

---

### Post by mkvnmtr on 2009-01-23
I have used Gparted off of the live disk to form and resize partitions on my G4 Ibook several times without issue. Not the installer just the partition editor in system. Works great. Whoever wrote and maintains Gparted does a great job. You installation should go smooth if you hit the tab key and type in live-nosplash powerpc. I think that was it. If not you will see it in the options.

---

### Post by dank28 on 2009-01-29
Thanks, mkvnmtr, live-nosplash-powerpc did the trick.  Installed 8.04 with no issues, and dual boot works great!  :p

This was my "test machine" because it's now going to be my wife's main computer (NO MORE FIXING WINDOWS EVERY DAY!)

I'm trying to do the same with my PowerMac, but having different issues, but that's detailed on another thread.

Anyway, for what it's worth I had zero issues repartitioning with GParted and installing a dual boot setup (OSX 10.4 & Ubuntu 8.04) on the G4 Mini.  :)

---


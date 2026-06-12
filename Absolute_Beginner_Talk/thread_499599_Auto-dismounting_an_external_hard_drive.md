---
title: "Auto-dismounting an external hard drive"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by trudetski on 2007-07-12
Hi, I'm running Feisty Fawn and I have a Seagate FreeAgent external HDD. I've got ntfs-3g working just fine and I can get the drive to auto-mount on startup and if I just plug it in while Ubuntu is running. What I can't seem to do is get it to dismount on shutdown and when Grub tries to load back up on reboot I just get a flashing white line in the top left corner. I assume it is waiting for the drive to start back up which it can't since it never turned off. I am sure there is some kind of tool or some sort of custom script that I could add to the shutdown process out there that would be able to tell my drive to dismount as Ubuntu is shutting down but I don't know where to look. Any help would be great.

---

### Post by KyleBrandt on 2007-07-12
I would first try dismounting in manually with command line to see if that is actually the problem before I worry about making a script.  Is grub/feisty fawn installed on the external drive?  I have a FreeAgent Drive as well, and I installed pmount, sudo apt-get install pmount, which I find a more convient tool for mounting and dismounting.  To dismount the drive with that, type mount, see what the device name is, and type pumount *device*.  In my case it is pumount /dev/sda1

---

### Post by Hendrixski on 2007-07-12
if you can unmount it from commandline then just save those commands to a file and save them as a script  ... then add the script to run when you **** down....

BTW... I see from your bean count that you're new... sooo...

WELCOME TO THE COMMUNITY!
We're all here to help new Ubuntu users because we love ubuntu, and we want to share our joy with others. 

If you prefer chatrooms then you should totally check out the channel #ubuntu on IRC.  Installing IRC is easy and fun.  Just go to applications-->Add/Remove and pick XChat from the list, click OK and you're done.

You can meet other Ubuntu users in your area too!  Just check out the Ubuntu LoCo teams for your city or state.

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it.  A lot of it is written by the same people who answer questions on these forums.  If dry manuals aren't your thing then relax and watch some videos.  [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc.  Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---


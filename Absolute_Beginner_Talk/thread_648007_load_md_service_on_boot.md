---
title: "load md service on boot"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Davidbmck on 2007-12-23
Hi!

New to Ubuntu (and linux, truthfully). I'm trying to set up a RAID-0 array, got it all working now :D except I find that if I want to use it, I have to do something like the following every time I start the computer:

sudo modprobe md
sudo mdadm --assemble /dev/md0
sudo mount /dev/md0 /media/Storage

I've added the /dev/md0 device to fstab, but it craps out on boot because I don't think the md service is running yet. How can I automate this? I want to move the home dir to this partition when I get it working properly, but I can't do that until it's loading on boot.

---

### Post by blueridgedog on 2007-12-23
You can place the commands in /etc/rc.local.

You can edit the file with sudo vi /etc/rc.local, replacing vi with a text editor of your choice.

You may have to mount it manually, as I believe drives in /etc/fstab have been mounted by the time rc.local runs.

You will want to put your commands prior to the "exit" point.

---

### Post by Davidbmck on 2007-12-23
Thanks for the help!

Do the commands in rc.local get executed at system boot, or at user logon? What I hope to be able to do is move the home folder to the raid-0 partition, so if these commands are run at user logon that won't work (ie: the /home/ folder won't exist when i try to log on, so Gnome will cry)!

I'll give it a go, see what happens.

Update: Half way there! I can get the md service running this way, and assemble the RAID partition, but I still need to mount it manually, like you said. :S So no good if I want to put the home folders there, the partition needs to be mounted before I log on.

---

### Post by blueridgedog on 2007-12-23
I was afraid of that, perhaps some others will come up with another idea.

---


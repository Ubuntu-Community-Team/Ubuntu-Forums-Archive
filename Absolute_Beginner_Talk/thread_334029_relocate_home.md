---
title: "relocate /home"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-08
This was all very clear when I started but now it is a confused mess.
The idea is to replace /home with a new one on a second hard disk. All of my info would then be on the second drive. A part image of the first drive and backups of the new /home would cover all the bases.

So far:
 I fortmatted the second drive as ext3 
sudo mkdir /mnt/home2
mount -t ext3 /dev/sdb1  /mnt/home2
chmod 777 /mnt /home2
copied everything from /home to /home2

This is where it got confusing.  I think /home is a root directory. /home2 isn't. The plan was to remove /home or rename it something and move or remount /home2 to be the new /home after renaming it. Then remove the old /home  

Maybe my wife is right. I'm short a marble or two.

Maybe someone with a lot more linux moxy can clear away some cobwebs.

Don't ask why. I don't know. It just seemed like a good way to get data off by itself.

Thanks

---

### Post by taurus on 2007-01-08
I assume you are the only user on your machine!  Instead of copying /home over to the new drive, why not copy /home/**your_username** over!

Maybe this guide would give you a hint.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by squrl on 2007-01-08
I did just that. squrl is a sub of /new_home. 
You jiggled a cell or two and I think maybe I am getting the picture.  

Thanks Taurus.

Guess I can't do that. Your referenced site says it is for advanced users.

---

### Post by squrl on 2007-01-08
A new approach.    

Copy over all of /home to the new drive. 
mount the new drive in /etc/fstab as /home. 
rename the old /home 

Reboot and hope the programs can find the new home :)

if it works then rm the renamed old /home

Will it work???

---

### Post by taurus on 2007-01-08
When you copy files over to the new drive, make sure the permissions and owner are correct or you won't be able to log in...

---


---
title: "Can't Get My Ubuntu to see XP boxes"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-20
This is kinda confusing, I hope that I explain it right.

First off, I setup Samba by these instructions here...
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I should say that I have 2 Ubuntu Fiesty desktop boxes on my network that I used this EXACT SAME procedure for and they are both working fine. I have 2 other XP boxes on my network and all 4 boxes can see each other, trade files, share, full access, etc...

So I put Ubuntu on my laptop last week and I did this exact same procedure. I cannot even see one of my XP boxes on the network at all. I also have Virtualbox running XP on this laptop and I cannot access that XP share from this laptop either. From the virtual XP on this laptop, I can see my Ubuntu desktop share fine, but I cannot see this Ubuntu laptop. 

I am running wireless on the laptop and I thought maybe this is why the desktop boxes can't see it, because I had this same problem while running XP (XP desktops couldn't see the wireless laptop). However, this doesn't explain (I don't think) why the Virtual XP session under this Ubuntu laptop (which is NAT'd) can't see the Ubuntu OS on the same machine. Maybe I am wrong...

Anyway, it appears that Samba is simply hosed on this box, but I don't know how to fix it or exactly what is wrong. I guess that I could try hooking up the hard-line and see if this helps anything, would wireless cause this kind of problem?

---

### Post by ugm6hr on 2007-07-20
Wireless itself shouldn't cause a problem.  However, I think that how-to doesn't cope with DHCP, which is a common way of assigning IP for wifi.

This is what I did:
[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

Someone has confirmed it works with Ubuntu too:
[http://ubuntuforums.org/showthread.php?t=500770](http://ubuntuforums.org/showthread.php?t=500770)

---

### Post by kc5hwb on 2007-07-20
I'll give that a shot.  However, even though I am technically on DHCP, I have my router set to assign a specific IP to each MAC that attaches to the network.  So yes, as far as the OS goes, it thinks it is DHCP, but the wireless router gives it the same IP each time I connect at home.

---

### Post by kc5hwb on 2007-07-20
ok, I tried this and it doesn't seem to want to work.  I might be doing something wrong, Xubuntu must have different menus than Ubuntu running Gnome, which is what I have.

PvNeighborhood finds my other machines on the network, but when I try and go to the shared folders, it always says "unable to mount"

---

### Post by ugm6hr on 2007-07-20
> **kc5hwb said:**
> ok, I tried this and it doesn't seem to want to work.  I might be doing something wrong, Xubuntu must have different menus than Ubuntu running Gnome, which is what I have.

PvNeighborhood finds my other machines on the network, but when I try and go to the shared folders, it always says "unable to mount"

Are you running pyNeighborhood as root (that was the point of the panel launcher - to make an easy way to start file sharing):
```
gksudo pyNeighborhood
```

---

### Post by kc5hwb on 2007-07-20
No I wasn't, that was the problem.  After I installed PyNeighborhood through Synaptic, it put the icon in my Applications menu.  I just ran it from there.  I guess I need to figure out how to make an icon for it using root.

Also, I cannot write to the folder I shared on my desktop from my laptop.  I assume this has something to do with the permissions on the local folder that the share is mounted to.

---

### Post by Panzor on 2007-07-20
My guess would be that your laptop made its own workgroup. Be sure to put all of your PCs in the same workgroup or Samba will throw up on you :P.

---

### Post by kc5hwb on 2007-07-21
> sudo gedit /etc/samba/smb.conf


In this conf file that I created, I put in the same workgroup as the rest of my network.

Also, I tried to update the title to "Can't get my Ubuntu to see ANY network machine"  I also cannot see my other 2 ubuntu boxes when I go to Places ->Network.  I see my NETWORK name listed, but nothing underneath this icon.

---

### Post by ugm6hr on 2007-07-21
> **kc5hwb said:**
> No I wasn't, that was the problem.  After I installed PyNeighborhood through Synaptic, it put the icon in my Applications menu.  I just ran it from there.  I guess I need to figure out how to make an icon for it using root.

Also, I cannot write to the folder I shared on my desktop from my laptop.  I assume this has something to do with the permissions on the local folder that the share is mounted to.
Not sure if you're still interested in pursuing pyNeighborhood...

Did you find that *gksudo pyNeighborhood* worked from Terminal?  If so - I think Ubuntu has a Menu Editor somewhere, that should allow you to change the "run" command for the menu entry to *gksudo pyNeighborhhod*, or you could create a separate panel program launcher like I did.  Unfortunately, I am not really very familiar with GNOME/Ubuntu, but I'm sure it will be quite easy.

As for the "write" permissions - is the shared folder on a Ubuntu or XP box?  In XP - there is a tick-box to allow network users to write to the drive.  In Ubuntu - "Shared Folders" - untick the read-only box in Properties.  If the share is already read/write enabled (and you can write to it from other networked computers), then it may be the write permissions for the path that you have mounted it to.  

So - where have you specified the mount point for the network drives in pyNeighborhood?  If it's in /home/*user*, then this will not be the problem.  If not - you have 3 options:
1. Just change the mount-point to /home/*user*/network (or something similar)
2. You can always have to run nautilus as root to write to the network drive (this may be a sensible option if you don't want to risk accidentally deleting / modifying the contents of the network drive) - *gksudo nautilus* from Terminal (or have a panel launcher / menu entry to reflect this command)
3. Change the permissions on the mount-point: *sudo chown -R **user:user** /media/network* in Terminal where ***user*** is your login and *media/network* is your chosen mount-point.

Hopefully, that should get your laptop up and running on the network, until you find a better solution.

PS: Don't forget to use *nautilus* instead of *thunar* in my example linked in previous post.

---

### Post by kc5hwb on 2007-07-21
I don't necessarily mind using PyNeighborhood, but I have become accustomed to cmd line with Linux.  My other 2 Ubuntu boxes on this network worked perfectly with the same setup link I copied into this first thread.  For some reason, it just didn't work on my laptop.

So to answer your questions....
This shared folder is on an Ubuntu box.  I have already unticked the "read-only" box on this folder, which is why every other machine on the network can write to it.
I changed the permissions on this folder on the shared box so everyone could see it and write to it
```
sudo chmod -R ugo+rwx /sharedfolder
```
I also ran this same command on the local mount point folder so that everyone could read/write/execute to it.  I am still having the same problem.

---

### Post by Irony on 2007-07-21
Make sure you enable your windows/norton/macafee or whatever firewall to allow your new laptop.

---

### Post by kc5hwb on 2007-07-21
neither of these boxes are on windows.... both ubuntu

---

### Post by ugm6hr on 2007-07-21
> **kc5hwb said:**
> I also ran this same command on the local mount point folder so that everyone could read/write/execute to it.  I am still having the same problem.

Try 
```
gksudo nautilius /*mountpoint*
```

If you can write to the drive like this (try copying and pasting a file), it is clearly a permissions issue - it will at least give you a clue.

---

### Post by kc5hwb on 2007-07-21
I need to go downstairs and boot my laptop and try that.  I still wonder why the other setup I listed in the first thread isn't working with the laptop on a wireless connection, since it works perfectly on 2 other hard-wired boxes on the same network.  :confused:

---


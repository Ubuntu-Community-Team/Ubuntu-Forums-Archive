---
title: "Can someone take a look at this Fstab"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by vatechtigger on 2007-04-07
Here is a screenshot of my fstab and my drives. 

WIn-Ubuntu does not show up. I can slick on it (note its grayed out in gparted) click mount but it does not show up.

WindowsBoot if I click mount pops up an error saying will not mount because ./media/WindowsBoot does not exist. (looks like it does to me)

Any ideas what Im doing wrong. All this worked before the autoupdate to 2.6.14

Mucho Gracias

---

### Post by STREETURCHINE on 2007-04-07
you should replace fat32 with vfat here is how i fixed it with my fat 32 partition

> /dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0

obviously change harddrives and mount points to suite  yours

Save it. Now, create a new mount point and mount it.

Code:

sudo mkdir /media/hda1
sudo umount /dev/hda1
sudo mount -a
df -h

---

### Post by Robynsveil on 2007-04-07
> **vatechtigger said:**
> Here is a screenshot of my fstab and my drives. 

WIn-Ubuntu does not show up. I can slick on it (note its grayed out in gparted) click mount but it does not show up.

WindowsBoot if I click mount pops up an error saying will not mount because ./media/WindowsBoot does not exist. (looks like it does to me)

Any ideas what Im doing wrong. All this worked before the autoupdate to 2.6.14

Mucho Gracias

Only new to this myself - *love* your desktop and how the Nautilus windows are semi-transparent... how did you do that??

---

### Post by vatechtigger on 2007-04-07
StrretUrchine:

can you describe the last two lines of code and what its for?
-a?
df -h?

thanks


Robynsveil:

Beryl Desktop. Just find it in add/remove and add. Then get the themes. Seems like it needs a good bit of graphics hardware. When running it and a game (xmoto) there is a bit of stuttering. And my pute is pretty descent (2gb ram, athlon 3700+, Geforce 7800GT)

---

### Post by STREETURCHINE on 2007-04-07
-a not to sure about that one but i guess it is telling it to mount the drive you just made the mountpoint for,

df -h    it is just to see if it mounted ,and were it mounted

---

### Post by LaurelLynn on 2007-04-07
Dear vatechtigger,

The triangular yellow sign with the exclamation point is telling you there was a problem mounting the drive.

What immediately springs to mind, is that you are mounting with the ntfs-3g drivers.

Those don´t come with the operating system, they have to be downloaded separately.  You can get them with apt-get or Synaptic, but you need to add some repositories. I would go to the project website for instructions (to find it you can goto SourceForge.com, the download page has a link to the project website).

Laurel Lynn

---

### Post by vatechtigger on 2007-04-07
LauraLyn,

I do have the ntfs-3g drivers. When they installed they updated the fstab file and changed that reference. Everything was working great until ubuntu autoupdated to 2.6.14. If I boot to 2.6.13 in grub everything is back to hunky dory. 


I think as a last resort I will unistall and reinstall them, also remove extra drives and add them one by one till I get everything set up again.

---

### Post by LaurelLynn on 2007-04-07
You took the words right out of my mouth ¨uninstall and reinstall¨

Laurel Lynn

---

### Post by vatechtigger on 2007-04-08
OK, basically I cleaned up the fstab by removing the UUIDs and changing the fat32 reference to vfat. All is working fine now. Seems to be a bit of rumbling in the community about UUID in the first place. All is well on my desktop though! Thanks guys

---


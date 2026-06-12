---
title: "permissions sharing samba"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Twiggy003 on 2007-11-03
Ok, Ive tried looking around on the forums and briefly google, but I can't seem to figure out why this is so:  Basically (on Gutsy) I right click on a folder (on an NTFS partition) and upon going to share folder it says 

" error accessing 'file:///media/hda2/Music': Access denied "

as root it does the same, on feisty it worked, I simple just right clicked share as, SMB etc.

ive tried changing permissions of the folder itself and such, but even has root it doesnt want to change, it says only root and plugdev can even access it, despite the fact as a normal user I can access/read/write to it locally, but it won't let me share.

Any ideas?

Thanks.

---

### Post by myk.dinis on 2007-11-03
Hrmm...are you using k or u? If u try installing gsambad...then you'll need to configure it properly...

The sharing in ubuntu is meant to be easy for entry level linux users...
But it's highly configurable for non-neophytes...you just need to know where to look...

/etc/samba/smb.conf

Are you dual booting?
regardless...do you have a seperate /home or is it on the same partition as / ?

You could always mount that drive...
Make a folder called ~/Shared
mkdir ~/Shared
Now you want to make a backup of you fstab...
cp /etc/fstab /etc/fstab.bak
Now you want to specify a mount point in your fstab pointing from that drive into that folder... Replace the ~/Shared with whatever you wanted to name the mount point <folder you wanted to share> 
echo "/dev/hda2  ~/Shared ntfs defaults 0 2" >> /etc/fstab
Reboot... 
sudo shutdown -r now
Then you'll be able to point to that folder with the sharing utility! 

Cheers!

Myk

---

### Post by Twiggy003 on 2007-11-04
Ubuntu Gutsy.  Ive tried using GSAMBAD, don't quite understand it all, I can't say ive tried properly, but so far I havent had much luck, i'll try again a tad later.

---

### Post by Twiggy003 on 2007-11-11
/home is on the same partition and I am booting between Ubuntu 7.10/XP/Gentoo and:

/dev/hda2 	/media/Music		ntfs	defaults	0	2

didn't work (fstab)

---


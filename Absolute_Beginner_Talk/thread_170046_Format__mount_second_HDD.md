---
title: "Format / mount second HDD"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by bonefishchris on 2006-05-03
I've got stuck trying to format and mount a second HDD. It's just there for extra storage or backup. It seems to have formatted OK and shows up as hdb1. However it does not appear in the Computer folder. 

I've tried sudo mount /dev/hdb1 and it seems to mount but still not show up anywhere useable. I'm gessing it may be to do with the mount path. 

Could anyone point me in the right direction please?

---

### Post by NeghVar on 2006-05-03
You will need to add it to your Fstab file.

Easiest way is this, go to your terminal:

cd /media
sudo mkdir hdb1 (you can make this supercalifragalisticexpealidotious, it doesnt really matter)
sudo gedit /etc/fstab (This is for gnome, sorry I dont know the comparable editor in KDE if your using it)

For detailed in structions on fstab i advise this site:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

For my second Hard Drive which is an ext3 automounded 40 giger my line in fstab is:

/dev/hdb1 /media/spare ext3 defaults 0 0

The drive shows as hdb1 in disks but the file I have in my media directory is called spare which is where I mount it to.

Hope this helps

Edit:

After rereading your OP I see that yes it is your mount path that is incorrect. Ther above advice will get you there but just for your information you need to tell the drive where to mount, thats what the creating a folder does, it gives the computer somewhere to show the files. Sorry if its seems like I'm talking down to you, I'm really not. Just trying to tell you why it didn't work and hopefully point you in the right direction rather than just giving you the answer without showing you why something doesn't work.

---

### Post by bonefishchris on 2006-05-04
Don't worry. Far from being offended, I'm very happy to have it spelled out to me:D 

I ended up making a folder 'HardDrive2' in /home/<username> and setting the path to that. When I put it anywhere else I found I didn't have permission to write to the drive. In fact, as a single user, this is a very convenient place to have it.

I don't know what I would have done if there were other users and I wanted them to be able to write to the second drive. Perhaps I could have changed permissions somehow but I don't know how to do that. Otherwise, I could have given each a partition I suppose.

Anyway, it looks to be working fine for me at the moment, so thanks indeed for your help.

---

### Post by bonefishchris on 2006-05-04
Oops! I spoke too soon. I've just rebooted and the folder I created, HardDrive2, is locked and belongs to Root again. Any Idea how I go about re-assigning permission to me? :confused:

---


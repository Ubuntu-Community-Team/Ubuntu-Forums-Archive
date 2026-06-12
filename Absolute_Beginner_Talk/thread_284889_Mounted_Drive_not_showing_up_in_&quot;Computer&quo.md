---
title: "Mounted Drive not showing up in &quot;Computer&quot;"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by joshgtv6 on 2006-10-26
hello, I finally figured out how to mount a second hardrive and get everything to work almost 100%.  However i'm still having three problems

First, I can access the new HD in the /storage folder in the filesystem, but why is the drive no longer showing up under Computer like it used to? What i mean is it used to show up as an actual drive, now it just shows up as a sub folder in filesystem. 

Second, I added the the drive to the fstab file so it should mount on startup but I have to manually mount it everytime I restart the computer.

Third, I lose write abilities to this new drive on reboot I have to redo the cmod and chown commands each time.  

This is what my fstab file looks like:

  GNU nano 1.3.10             File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /storage        ext3    defaults 0 0

This is what my pmount allow file looks like:

# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
/dev/hdb1

Not sure what else you all will need to help with this.  I'm close to getting this back to the way it was a few days ago after an unsuccesful dual boot.  This is the last of the issues and it has me baffled.

---

### Post by taurus on 2006-10-26
1.  Only drives in /media will show up on your desktop.

2.  Change the last two numbers to "0   2"!

3.  You can set the permissions with "chmod"...

```
sudo chmod -R 777 /storage
```

---

### Post by kidders on 2006-10-26
Hi there,

> **joshgtv6 said:**
> First, I can access the new HD in the /storage folder in the filesystem, but why is the drive no longer showing up under Computer like it used to?
Ordinarily, getting rid of the silly "drive" icon is people's ultimate goal when plugging in new hardware on a permanent basis! It's exactly the way Linux likes it :-) After all, Linux has no concept of a "drive".

Your problem is a strange one. First of all, you don't need to make any pmount modifications to have things work for you. Pmount is most likely the thing that is causing you trouble. To add a new filesystem to you Linux box, the only thing you need to do is modify /etc/fstab so it mounts in a sensible place for you. You should undo any other changes.

Hope that helps.

---

### Post by joshgtv6 on 2006-10-26
> **taurus said:**
> 1.  Only drives in /media will show up on your desktop.

2.  Change the last two numbers to "0   2"!

3.  You can set the permissions with "chmod"...

```
sudo chmod -R 777 /storage
```

ok, we are almost there now.  I made all these changes, and have the drive mounting to /media, changed the fstab with the (0 2) instead of (0 0). And it now mounts on boot and i get read/write privaledges. AWESOME! Now the only thing left is to get the new hardrive to show up here. I am putting a screenshot up to show where I want it to be.  It used to show up as a drive just like filesystem. Thanks for helping with this.  

[IMG]http://h1.ripway.com/jpeifley/screen.png[/IMG]

---

### Post by joshgtv6 on 2006-10-26
> **kidders said:**
> Hi there,


Ordinarily, getting rid of the silly "drive" icon is people's ultimate goal when plugging in new hardware on a permanent basis! It's exactly the way Linux likes it :-) After all, Linux has no concept of a "drive".

Your problem is a strange one. First of all, you don't need to make any pmount modifications to have things work for you. Pmount is most likely the thing that is causing you trouble. To add a new filesystem to you Linux box, the only thing you need to do is modify /etc/fstab so it mounts in a sensible place for you. You should undo any other changes.

Hope that helps.

yeah, i wasnt' sure about needing it in pmount either, but I was trying to follow all the guides to a "T" and some said to edit pmount, others didn't. But i removed it from pmount as well now and did what Taurus said and it's working great.  Except for the last problem which you can see in the post above this one.  Any ideas on that would be appreciated.

---

### Post by taurus on 2006-10-26
I am at home right now and using Gentoo at this moment but you can always create a link to your Computer!  Look in the menu on top to see if you can find it there.  If not, let me know and I will look it up for you when I get into the office after lunch.

---

### Post by joshgtv6 on 2006-10-26
> **taurus said:**
> I am at home right now and using Gentoo at this moment but you can always create a link to your Computer!  Look in the menu on top to see if you can find it there.  If not, let me know and I will look it up for you when I get into the office after lunch.

yeah, i'm still having an issue with it.  In another thread someone had mentioned something about navigating to Nautilus under Apps and to check a tick box to show volumes but I don't have Nautilus listed under apps.  At least not under the drop down menu at the top of the screen.  So any further help would be appreciated.  Normally it wouldn't matter but it's just frustrating because I know i had it showing up there a few days ago and now it's not.  I'm sure you can understand.

---


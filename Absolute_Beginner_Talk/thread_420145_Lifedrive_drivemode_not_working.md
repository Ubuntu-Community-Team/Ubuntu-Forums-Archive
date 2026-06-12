---
title: "Lifedrive drivemode not working"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by jasonk on 2007-04-23
I just installed fiesty and i love it.  my only issue is that now my lifedrive won't show up in drive mode.  The folder used to mount and show up on the desktop in edgy, but it won't now.  It looks like the drive thinks it's connected, and it will charge, but i can't find the mount folder anywhere.
thanks.

---

### Post by jasonk on 2007-04-24
Ok, here's an update.  I found this link to a bug report, [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/89723]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/89723")  and i followed the steps to manually mount my lifedrive.  When i typed, sudo mount /dev/sdc1 /mnt , it mounted and i was able to get files off of it.  now how do i get this to happen automatically.  i really don't want to have to type that in everytime.  is there something i can do.  thanks

---

### Post by jasonk on 2007-05-02
ok, i got the lifedrive to sync, but i still need drive mode to work.  now when i try to mount it manually with "sudo mount /dev/sdb1 /mnt"  it's telling me "you must specify the filesystem type"  can anyone help me with this?  I don't know how to do that.  Also is there any way to sync my evolution inbox with the inbox on my pda?  thanks.

---

### Post by jenningsghv2 on 2007-05-05
Hi to all. While I'm enjoying my time with Feisty Fawn, unfortunately I find myself in the same dilemma with LifeDrive's Drive Mode not being recognized. The weird thing is that Drive Mode was working perfectly fine with Edgy Eft. What could've become broken here?

---

### Post by jenningsghv2 on 2007-05-05
Hi again. Just a quick follow-up. After the posting the preceding message, I explored my Feisty fawn directors, specifically the /media folder and lo and behold--the contents of the LifeDrive in Drive Mode were there, apparently with complete read/write access. I tested this by opening a document file straight from the LifeDrive, and then copying a text file which I then opened from the Palm handheld. Apparently, it transfered correctly as the notes in the text file were there.

I'm not sure why is this the behavior now, which is different from Edgy Eft (where the drive was mounted and one needed to eject it after use), and I'm not sure if this change would have any impact on the LifeDrive's microdrive. Looking forward to any heads-up from the community, although--again--I'm thrilled to be able to transfer files to/fro Feisty Fawn and the LifeDrive.

---

### Post by jasonk on 2007-05-14
I wish i knew how you got it to show up in the /media folder.  mine doesn't show up there, or anywhere that i can find.  Do you use a cradle or just a cable to connect?

---

### Post by rob2nd9th on 2007-08-12
> **jasonk said:**
> Ok, here's an update.  I found this link to a bug report, [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/89723]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/89723")  and i followed the steps to manually mount my lifedrive.  When i typed, sudo mount /dev/sdc1 /mnt , it mounted and i was able to get files off of it.  now how do i get this to happen automatically.  i really don't want to have to type that in everytime.  is there something i can do.  thanks

Iv tried this to no availe?? Has any one found out why this has stoped working on this release?

---

### Post by bapoumba on 2007-08-12
> **rob2nd9th said:**
> Iv tried this to no availe?? Has any one found out why this has stoped working on this release?
I'm with you on this one. I have not been able to use my palm either with feisty or gutsy. I've tried jpilot, gnome-pilot, the visor modules (that make the palm go into an infinite reboot process) etc.
I now think, but I do not understand it, that it is a hal issue. I cannot go anywhere further. I quite miss to be able to sync the palm and use it for storage. I bought it because it was supported... *sigh*.

---

### Post by rob2nd9th on 2007-08-12
[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

used this and got my lifedrive to synk with jpilot (two go's)

---

### Post by altongary on 2007-09-05
:guitar:Here's what I did to get my lifedrive's hard drive to show up like a usb flash drive:
1. Connect your lifedrive to the computer and enable drive mode.
*Before I got this working, this is where I'd have access to the sd card, but be unable to mount the lifedrive's hard drive.*
2. Open a terminal and type: SUDO BLKID
    *Note the output. You're looking for LABEL="LIFEDRIVE" To the left of that is the device name that you want--In my case it was /dev/sdb1. Write it down and save it for later!*
3. Type: SUDO MKDIR /MNT/LIFEDRIVE *This makes a mountpoint for your lifedrive. At this point, you could type: MOUNT /DEV/SDB1 /MNT/LIFEDRIVE (and vice versa for umount) to be able to see the files on the lifedrive's hard drive when you open the folder /mnt/lifedrive. However, only root will have read write access.*
4. Now type: GKSU {your text editor} /ETC/FSTAB. At the bottom of the file add:
/dev/sdb1       /mnt/LIFEDRIVE	vfat	user,noauto	0	0
Save the file, close your editor and logout.
5. Log back in and put your lifedrive in drive mode. It should now mount properly.

---

### Post by bapoumba on 2007-09-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/81219](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/81219) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks altongary.

So I tried your suggestion. It works only one time for me. If I disable the drive mode on the Lifedrive, and enable it again, the /dev/sd*1 changes. It mounts only if I edit /etc/fstab accordingly.

Any idea ?

---

### Post by altongary on 2007-10-12
Hi:
I didn't look into it further because I haven't had this particular bug happen to me -- I'm new at this whole linux thing and was pretty surprised I got it to work. On the other hand, if anyone can tell me how to get my Lifedrive to consistently sync with my computer I'd be eternally grateful.:confused:

---

### Post by bapoumba on 2007-10-12
> **altongary said:**
> Hi:
I didn't look into it further because I haven't had this particular bug happen to me -- I'm new at this whole linux thing and was pretty surprised I got it to work. On the other hand, if anyone can tell me how to get my Lifedrive to consistently sync with my computer I'd be eternally grateful.:confused:
[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)
This is what I used to sync. I tweaked the **/etc/udev/rules.d/10-custom.rules** file a bit to insert my own palm serial number, but the basic one works.

---

### Post by AlfyBoy on 2007-11-11
Thanks to altongary for

> Here's what I did to get my lifedrive's hard drive to show up like a usb flash drive:
1. Connect your lifedrive to the computer and enable drive mode.
Before I got this working, this is where I'd have access to the sd card, but be unable to mount the lifedrive's hard drive.
2. Open a terminal and type: SUDO BLKID
Note the output. You're looking for LABEL="LIFEDRIVE" To the left of that is the device name that you want--In my case it was /dev/sdb1. Write it down and save it for later!
3. Type: SUDO MKDIR /MNT/LIFEDRIVE This makes a mountpoint for your lifedrive. At this point, you could type: MOUNT /DEV/SDB1 /MNT/LIFEDRIVE (and vice versa for umount) to be able to see the files on the lifedrive's hard drive when you open the folder /mnt/lifedrive. However, only root will have read write access.
4. Now type: GKSU {your text editor} /ETC/FSTAB. At the bottom of the file add:
/dev/sdb1 /mnt/LIFEDRIVE vfat user,noauto 0 0
Save the file, close your editor and logout.
5. Log back in and put your LIFEDRIVE in drive mode. It should now mount properly.

On my case, to mount my LIFEDRIVE on Gutsy, I just tweak that to this:

First put it to USBdevice, connect it, and:

```
sudo blkid
```

to see where is LIFEDRIVE, then:

```
sudo mkdir /mnt/LIFEDRIVE
```

If LIFEDRIVE is on sdb1 then code, 

```
sudo mount -t vfat /dev/sdb1 /mnt/LIFEDRIVE
```

not beeing that the case code whatever came at the left when you typed "blkid", after that, you can see on your directory /mnt/LIFEDRIVE your files.

to umount type:

```
sudo umount /dev/sdb1 /mnt/LIFEDRIVE
```

(remember to change sdb1if your LIFEDRIVE is not there)
and that's it :)

---

### Post by altongary on 2008-03-08
<See my earlier post; make the directories and copy all of the info about your lifedrive given by sudo blkid>
After installing Kubuntu Gutsy on a new hard drive, I ran into Bapoumba's bug, where the device location of the Lifedrive is inconsistent. I think I may have found a solution. FSTAB provides multiple ways of mounting a device. Instead of using [/dev/sdb1 /mnt/lifedrive vfat user,noauto 0 0] in /etc/fstab, you can use:
[UUID=YourLifedrive'sUUID /mnt/lifedrive vfat user,noauto 0 0]
[LABEL=YourLifedrive'sLABEL /mnt/lifedrive vfat user,noauto 0 0]
[/dev/disk/by-id/YourLifedrive'sID /mnt/lifedrive vfat user,noauto 0 0]
You are probably wondering where you can find these -- UUID and LABEL should be listed with sudo blkid. 
"/dev/disk/by-id/YourLifedrive" can be found by navigating to /dev/disks in Konqueror and looking in the /by-id folder The correct IDs for your device should be obvious i.e. usb-palmOne__File_storage_PalmSN12345678-0:0-part1. Make sure you use the IDs that end in -part1. I used /dev/disk/by-id because it was the only way besides listing a specific device location to get fstab to see my Lifedrive. 
After you're done editing /etc/fstab logout and log back in.
Put your Lifedrive in Drive Mode-- if your system is like mine, then you've just discovered that your Lifedrive is still not automounting. Fortunately, Kubuntu has come to the rescue with an adequate compromise.
1. Right click on the desktop.
2. Navigate to Create New Link By Device -- MO Device.
3. Choose a name and pick a mounted device icon.
4. Click the Device tab and look in the dropdown menu-- you should see the id for your Lifedrive. Select it and choose an unmounted device icon. Hit OK.
Repeat steps 1-4 for the Lifedrive SD card.
You should now have icons on your desktop that allow you to mount and unmount your Lifedrive's disks when it is in Drive Mode.

---

### Post by jjwoznia on 2008-05-15
I am running ubuntu hardy and I just got a lifedrive. I couldn't get the drive mode to work. I stumbled upon this thread after a I found a few other blogs. This is how I got drive mode to work.

1. Turn on the drive mode
2. Then run 
```
sudo blkid
```
3. Then made a directory for the mount
```
sudo mkdir /media/LIFEDRIVE
```
4. Using the conventional /dev/sd**, I wrote an fstab line
```
/dev/sdi1 /media/LIFEDRIVE vfat user,auto,rw 0 0
```
5. Log out and log in
6. In order to mount the drive, I use the drive mounter applet that you can put on your panel. 


I couldn't find a way to auto mount the drive. I don't have the card mounted either, just the internal storage. I'm going to look into it  a little more, because this is obviously not the ideal fix.

---

### Post by bapoumba on 2008-05-15
Thanks. I would really like to be able to use the 4Go storage again. This is one of the reasons I bought it.
The most frustrating part is that it worked out of the box with dapper.. 

With hardy, it does not automount and I could not get it to sync with the fixes that worked on gutsy.
I plan to see if I could get it to work with wifi or bluetooth, but had no time to look into it yet.

---


---
title: "iPod Nano will not mount"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Davehogs on 2007-06-27
HELP would be very much appreciated by this rookie.

Did a very basic post about this in the wrong are so I figured I'd stand a better chance by a more complete post in the correct area.

From reading other posts it sounds like I made a very common mistake ..overconfidence.. act first without knowing what I was doing and then trying to do damage control (unsucessfully). Trying to wean myself off of Microsoft ( a really expensive habit and monkey to get off of my back) and set up my Ubuntu box. Have a good skill set on DOS and every version of Windows from v3.0 to XP. Vista was the end of Windows for me after I saw the direction Microsoft is headed toward.

Did everything email..browser.. contacts... bookmarks etc no problem except for importing  messages from Outlook Express 6.0.  No real problems until I tried to get my 8GB iPod Nano to work properly with GTKPOD. Did the search on the forums and with the Ipod mounted I left clicked on the icon on the desktop , selected properties, the drive tab and edited the mount point. Keyed in the mount point of /media/iPod as seems to be common in most of the posts about iPod problems and created the /media/iPod directory.  the  changed the mount point to the /media/iPod setting recomended and from terminal did the created the directory with the  - sudo mkdir /etc/iPod. 

Bad move. Screwed up by not writing down the default settings before I changed them. Now Ubuntu recognizes the iPod yet will not mount it. Trying to figure out what to do to fix it without doing a full reinstall and seem to be just digging a deeper hole. Not made any changes to the mtab file and other than removing a line I added to the fstab file suggested from a post have not damaged my system any further. Ordered "The Ubuntu Bible" before I even started setting up my Ubuntu box.. Looks like I should have waited until I received the book and did some reading. Book should be here tomorrow when I get home from work.

"If you find yourself in a hole..STOP DIGGING!" 

 Anybody know how to undo the damage I have done? 

-Dave

---

### Post by Maxtorm on 2007-06-27
What suggestion made you want to move the default moint point for the iPod?  Since mount points are arbitrary, GtkPod should have been able to find it no matter where it was mounted.  YMMV, but I would shut the machine down, disconnect the iPod, start the machine again and remove the directories you created:
```
sudo rm -rf /media/iPod
sudo rm -rf /etc/iPod
```
Then connect the iPod.  It should mount automatically as it did before.  Right-click on the iPod icon that appears on the desktop and choose Properties.  Remember the mount point, but don't change it.  Install Amarok (in my estimation, a much better program for managing media and your iPod).

---

### Post by Davehogs on 2007-06-27
Did everything as you suggested. And still no mount.

Here is what is in my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b99b72d7-4950-48d7-8e74-47fe1f1f99bf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=853d83ac-78ea-4eba-9c18-e8ef93d610e4 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

Noticed when I plug the cable into the nano that 3 files show up in the /dev/ subdirectory

usb-Apple_iPod_000A270018E1247E-0:0
usb-Apple_iPod_000A270018E1247E-0:0-part1
usb-Apple_iPod_000A270018E1247E-0:0-part2

Link Targets are sdf, sdf1 and sdf2 . 

Ubuntu sees the Nano yet it will not mount it.

Did I kill a line in the /ect/fstab on how to deal with the device when I was undoing the change suggested in the forum message I read?

-Dave

---

### Post by moore.bryan on 2007-06-27
[I]your nano shouldn't show-up in fstab, afaik...
have you tried having your ipod plugged in as your boot your computer?
[/I]

---

### Post by Davehogs on 2007-06-27
Thanks Bryan,

Had been playing around with the fstab a little bit and had success at mounting the iPod .. did quite a bit of learning in the process. But wouldn't unmount properly. Read your message and couldn't believe it could be that simple.. .. removed the line I was playing with in the fstab and gave your suggestion a try .. it worked immediately ... Dah.. the "plug n pray" actually works in Ubuntu. Actually made sense as it is a USB device. 

Thanx again.. owe you one.

-Dave

---

### Post by moore.bryan on 2007-06-28
[I]just glad to hear you got the ipod mounting... they can be nasty little buggers when it comes to linux.  my 1st gen nano wouldn't work well with any of the linux programs (gtkpod, yamipod, etc.); it was always painfully slow, so i switched over to rockbox and couldn't be happier.
once again, just glad you figured it out.  best of luck.
[/I]

---

### Post by drkeuk on 2007-06-30
I had the same problem until I changed the mount point from media/ipod to media/IPOD. Try editing the path in gtkpod's Edit > Edit repository.

---

### Post by Davehogs on 2007-07-01
Lessons learned:

Changing the mount point of the iPod from the properties drive tab on the iPod, as long as a valid subdirectory is chosen when from the properties really matters little. Change the settings in Amarok or what ever to match and you won't have any problem. The root problem that I discovered is that changing the mount point of the iPod from the properties Volume tab on the iPod is a whole different matter. Put the exact same mount point you set the drive mount point to /media/iPod and you are dead in the water. The Volume mounting point cannot begin with a / .The iPod will not mount and you get the error message about the illegal character in the mount point. With the iPod plugged in .. click on Places, Computer.. right click on the iPod icon.. Properties..Volume tab.. and change the mount point to eliminate the leading /      ex. /media/iPod will me changed to media/iPod or even just media.. is all it takes to fix it. The mount point on the volume needs to be changed to eliminate the misleading prompt and I believe people would stop making the mistake. 

-Dave

---


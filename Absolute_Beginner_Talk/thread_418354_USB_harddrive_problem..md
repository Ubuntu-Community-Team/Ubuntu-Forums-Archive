---
title: "USB harddrive problem."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Dimicus on 2007-04-22
Hi guy's appreciate some help here. i beginn to say im a beginner. 

Problem. 

i had a USB hardrive that was working fine in Ubuntu fiesty fawn however i could not copy from or to it. After some search on internet i realise that the problem was that it was a NTFS filessytem on it that messed it up :) anyone before this i was playing around with it. 


Ok i can see the disk under X and i right clicked on it and chosed properties
and found i could manualy change the mountpoint there and i just had to try. printed in mountpoint "/media/Ny volym" that was the directory to it.  and now when i try to reach the disk
i get error. 

" unable to mount the volyme "Ny volym"

Details: Mount_point cannot contain the following characters:
newline, G_dir_seperator (usualy /) "

well here is my fstab.

-----------------------------------------------------------------------------------------------
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d162a043-8bab-436b-a420-3b0c5c89b72e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=83978619-4894-491c-882e-97b5a22866cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

-------------------------------------------------------------------------------------------------

i have tried to read on forums and faq how to use the fstab but honest. for someone that are totaly new those faq are hard to understand :) for example i d understand what cdrom etc is here but sda1 ? is that my boot harddrive ? and sda5 is that my second harddrive ? 
when i have seen other peoples fstab they dont have all this numbers "UUID=83978619-4894-491c-882e-97b5a22866cc"  in their fstab.

What should the USB harddrive be named ? and is it here i can change the mount point on it ? 
and if, HOW :) ?

best regards
/Dimicus

---

### Post by Happy_Man on 2007-04-22
I see... you've got a foreign character somewhere in that harddrive's name, which is screwing up Ubuntu, so it won't mount it. I suggest renaming it in XP and then coming back to Ubuntu and trying to mount it.

---

### Post by Dimicus on 2007-04-22
Hi thanx for answer, however it diden't work still same problem. and i choosed to name the drive to "hej", appreciate some more help.

---

### Post by vanadium on 2007-04-28
I now have the same problem for a fat32 formatted USB drive that used to work. It bears the volume label MEDIA and was mounted under /media/MEDIA. Then, I used that drive on another computer, where it was mounted also as media/MEDIA. When I reconnected the USB to the first computer, it was mounted to /media/MEDIA_ instead.

In the right-click menu of the drive, there is an option to change the mount options. I typed "media/MEDIA" for mount point and left the two other option fields blank. Then I unmounted the drive and it would not anymore mount, with this error message.

Probably this issue can be solved editing a configuration file. I am also looking for a solution.

---

### Post by vanadium on 2007-04-28
I found the problem, and rereading the original poster&#347; problem, also his.

* This is the url that helped me
[http://ubuntuforums.org/archive/index.php/t-376404.html](http://ubuntuforums.org/archive/index.php/t-376404.html)

* What you need to do:
- go to "Places - Computer"
- right-click your drive that won't mount and select Properties, volume tab.
- Under "Settings", clear the string in "Mount point", or fill in a single name (e.g. "Ny_volym" in case of the original poster). Remove and re-insert the drive.

The error we made is that we entered a path in the "Mount Point" box. Yet, only one label, the name of the moint point under media, and not a full path can appear here!

To the original poster: try whether a space works, but if you have trouble, use an underscore instead of a space.

If you leave it empty, the system will use the volume label. Otherwise, it will use any label you specify here.

If this works for you, then please add [SOLVED] to the titel of this thread.

---

### Post by Dimicus on 2007-04-28
ok i solved it thanx for all reply. 


the solution was to do this.

I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.

or

I launched gconf-editor and deleted the key for the ipod under /system/storage/drives/_org_freedesktop_Hal_devices_storage_serial_Apple_ ipod_*.

the solution was so easy ;(

---


---
title: "I just killed windows, no more dual boot :D"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-11-15
I got a virus on windows so I unmounted both my restore partition and NTFS windows partition with gksu thunar and with partitionar I made a FAT32 partition. I'm loving all the extra space!!

So, how do I get rid of the windows boot option from the bootloader?

Was this not a safe thing to to do?

sv

---

### Post by natehatewindows on 2007-11-15
well it makes sense to me that windows it totally gone so you could just do 

```
 sudo gedit /boot/grub/menu.lst
```

and at the bottom you will see something like:

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista(loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

and you could just delete this part. maybe read a bit more but this is what i would try.

---

### Post by TeaSwigger on 2007-11-15
Hello, I'm not a security expert to advise there, but it sounds ok to me; I'm curious why you reparitioned in FAT32 instead of Linux's native ext3?

To change the GRUB menu you can edit its configuration, in a text editor:

```
gksu gedit /boot/grub/menu.lst
```

or use GRUBed:

[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

Please do note that you don't want to make a bad mistake in that file since it needs to work to boot, so proceed methodically. :)

---

### Post by forestpixie on 2007-11-15
that's exactly what I did when I threw windows out of the ... window, you could, to be sure # all the lines that refer to the windows boot before you delete them

you might need to update grub, but I don't think so - just in case

```
sudo update-grub
```

> Was this not a safe thing to to do? I'd say it was the safest thing to do :)

---

### Post by staticvoid on 2007-11-15
THANK YOU ALL for your quick responces. I think I will take a look at GRUBed, TeaSwigger, and thats a very good Idea just to add # instead of deleting the whole line, forestpixie. natehatewindows, thanks for the peice of code to get to the boot menu code file :).

I'll post and tell you how it goes.

is it better to use ext3 over FAT32? I am very naive when it comes to this. I'm sure its highky technical, but, whats the dif? between ntfs, fat32, ext3, and that mac type....?

Static Void

---

### Post by KIAaze on 2007-11-15
ext3 fragments less, almost not at all actually. :)

---

### Post by natehatewindows on 2007-11-15
i would do ext3 because you dont have windows anymore :) and it would be better to do now then when you ave it half full and decide you should have done it......it is just  what KIAaze said.....fragments almosst not at all...stays clean. i would reformat to ext3 man!

---

### Post by TeaSwigger on 2007-11-15
> **staticvoid said:**
> THANK YOU ALL for your quick responces. I think I will take a look at GRUBed, TeaSwigger, and thats a very good Idea just to add # instead of deleting the whole line, forestpixie. natehatewindows, thanks for the peice of code to get to the boot menu code file :).

I'll post and tell you how it goes.

is it better to use ext3 over FAT32? I am very naive when it comes to this. I'm sure its highky technical, but, whats the dif? between ntfs, fat32, ext3, and that mac type....?

Static Void

You're welcome :) Yes it is better to use ext3. Better performance and better odds for clean recovery in the event of a problem. Although it is a Linux filesystem, if you do want to use windows with it in the future, you can get windows to access it by installing a (free!) driver in windows. :) GRUBed helped me early on in having more confidence learning that GRUB file, maybe it'll help you too. Once you get some understanding of it, it's easy to edit in a text editor from then on.

---

### Post by natehatewindows on 2007-11-15
oh an hey....about my post...

the # is part of the menu.lst file, you dont ad this you need to delete all these lines.

---

### Post by natehatewindows on 2007-11-15
> that's exactly what I did when I threw windows out of the ... window, you could, to be sure # all the lines that refer to the windows boot before you delete them

yes be sure they all are either the "Divider" crap or having to do with windows. and i dont think you need to update grub but it wont hurt,

---

### Post by KIAaze on 2007-11-15
Oh, and with FAT32, the maximum filesize is 4 GiB, while with ext3 it's 16 GiB to 2 TiB:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

It seems NTFS is better there, but since it's still not an open standard, you'd better use ext3.

edit:
Strange contradiction:
[http://en.wikipedia.org/wiki/NTFS]("http://en.wikipedia.org/wiki/NTFS") says max filesize=2 TiB for NTFS
while the [comparison table]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") states 16 EiB...

Anyway, use ext3. :P
A safe solution.

---

### Post by natehatewindows on 2007-11-15
i do have a usb hard drive formatted to ntfs, it works well but i hate that it does not delete files, yo have to show hiden files and manually delete them. if i could do it again i would format it to ext3, but now there is over 600gb on there and i have no where to put it. :(
maybe ill by another drive so i can! ;)

---

### Post by staticvoid on 2007-11-15
Ok, I'll repartition it as ext3.
I rebooted and just had to go into recovery mode. then I rebooted again and it got in correctly. now I have to manually mount my partition and enter a password.

 I have 20 gigs in that FAT32!  huh? I wonder how that happened then. I'll make it Ext3.

and thanx for the links :D

S.V.

---

### Post by staticvoid on 2007-11-15
What is Lost+Found? and why is 1.2 GB already used on ext3?

:D

lovin' ubuntu,
sv

---

### Post by natehatewindows on 2007-11-15
i have no idea what that would be,,,,,maybe just from the formatting?? im not sure....im sure you will get a good answer, :)

---

### Post by staticvoid on 2007-11-15
Hmm. Yeah, probably :) Since it is Ext3, I can only access the drive by root... can I change the permissions some how?
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-4.png[/IMG]
maybe in Gparted?

sv
[B]
EDIT: I CHANGED THE PERMISSIONS with GKSU THUNAR  :D[/B]

---


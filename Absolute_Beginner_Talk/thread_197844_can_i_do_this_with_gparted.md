---
title: "can i do this with gparted?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-16
ok i am rapidly running out of space on ubuntu i just had to sudo nautilus just so i could use the 3.6gigs from the documents folder with a new folder that i linked.

i have a spare 7gig that i was using a bridge between my windows xp part and ubuntu but now that i can access my winxp directly its not really needed. so if i go into gparted and unmount it and change it to a ext3 will ubuntu recognize it? can i add it to my home folder to increase its size?

this way ubuntu and xp would have the exact same space on my hard drive and space wouldnt be an issue to me.

is it possible to do that without messing up my current ubuntu config?

---

### Post by jak on 2006-06-16
I'm assuming that as you said you used the partition as a bridge from Win to Lin it must be read/writeable by both - meaning it must be FAT32 ?
Ubuntu can read/write FAT32 partitions just fine so you can mount the partition to use it. I tend to do it like this:

$sudo mkdir /media/shared
$sudo mount -t vfat /dev/hda3 /media/shared

where hda3 is the partition you want to mount.

It might be a good idea to put a symlink in your home directory to the partition so you can store files there easily.

$ln -s /media/shared /home/username/shared
 ( or the other way round.. I forget and I can't check as I'm on a public Windows system )

---

### Post by glotz on 2006-06-16
Your XP partition probably is a NTFS, which Ubuntu can read but not reliably write. Take that into consideration.

If you delete some partition and make an ext3 partition, Ubuntu can use it. However, as far as I know, you cannot use partition disk space seamlessly, unless you actually join the partitions, which has prerequisites, the partitions need to be adjacent on the disk. Maybe you could post a screenshot of gparted here. I might be wrong as I'm pretty new into Ubuntu and Linux myself...

Besides this partitioning to get more disk space, there are a few things you could do to scrape together some space. Have you emptied your package manager cache? Do you have kernels (and linked restricted modules if you're on nvidia card) you're not using? Do you have any use for all the fonts the default install comes with? (there's chinese and indian and god knows what fonts, worth of some 300 megs) And also see [http://www.ubuntuforums.org/showthread.php?t=140920](http://www.ubuntuforums.org/showthread.php?t=140920)

---

### Post by maddbaron on 2006-06-16
[QUOTE=glotz]Your XP partition probably is a NTFS, which Ubuntu can read but not reliably write. Take that into consideration.

If you delete some partition and make an ext3 partition, Ubuntu can use it. However, as far as I know, you cannot use partition disk space seamlessly, unless you actually join the partitions, which has prerequisites, the partitions need to be adjacent on the disk. Maybe you could post a screenshot of gparted here. I might be wrong as I'm pretty new into Ubuntu and Linux myself...

Besides this partitioning to get more disk space, there are a few things you could do to scrape together some space. Have you emptied your package manager cache? Do you have kernels (and linked restricted modules if you're on nvidia card) you're not using? Do you have any use for all the fonts the default install comes with? (there's chinese and indian and god knows what fonts, worth of some 300 megs) And also see [http://www.ubuntuforums.org/showthread.php?t=140920](http://www.ubuntuforums.org/showthread.php?t=140920)[/QUOTE]

nah xp part is fat32 I can save stuff there too manually but when it comes to downloading files or torrents I must save 2 an ubuntu file then move to xp.

how do I empty package manager cache?

nah I only use the fonts that r in the system only english. dont need the rest, how do I empty those?

I kno nothing about my kernals i just saw on this board how to add k7 b/c i am using an amd sempron. other than that i am clueless when it comes to kernals

what i really want to do is enable a directory in my xp or the other fat32 7gig so that i can access it with my music players and video players so i can save all my my media there directly and still be able to play them b/c when i try to do now the media players cant see those drives its very bothersome since music is taking up most of my /home folder. but getting rid of unneeded installed files would be great.

---

### Post by glotz on 2006-06-16
Open Synaptic (system > admin >) and goto settings > prefs > files > delete cache. Then exit the menu and select status display mode (in the lower left corner) and select installed and browse to see what all there is. There you will find the kernels and the fonts. Don't break your system by removing the wrong packages though... :)

If you goto system > admin > disks can you see the disk and partition the XP is on? Can you mount them? Now, if you could, do your music players function as hoped?

---

### Post by maddbaron on 2006-06-16
[QUOTE=glotz]Open Synaptic (system > admin >) and goto settings > prefs > files > delete cache. Then exit the menu and select status display mode (in the lower left corner) and select installed and browse to see what all there is. There you will find the kernels and the fonts. Don't break your system by removing the wrong packages though... :)

If you goto system > admin > disks can you see the disk and partition the XP is on? Can you mount them? Now, if you could, do your music players function as hoped?[/QUOTE]

thanks i deleted the cache got some space back couldnt delete any language files since there was only english from what i saw. 

here is my disk outlook the one highlighted hda4 is as u can see full of space. i'd want to make that my default music folder but i dont know how to change it so i can create a link since everytime i try i get an error even with sudo nautilus i can create files in there but not link them together. i even think when i clicked share after right clicking i installed samba...i dont even know what that is. anyway here is the image.

the 1st two parts r windows even tho the 1st part is only 3gig;s and i dont use it for anything i assume thats where my system bios is.

---

### Post by glotz on 2006-06-16
The fonts are called ttf-something. Look at the descriptions. (ttf as in true type font)

I want a screenshot of gparted. You mean the partition isn't automatically mounted or? What error do you get and exactly when? Samba is for sharing files between different computers, you don't need that for this.

Your BIOS is not anywhere on your disk as far as I know but on a BIOS EEPROM chip on your mobo.

---

### Post by maddbaron on 2006-06-16
[QUOTE=glotz]The fonts are called ttf-something. Look at the descriptions. (ttf as in true type font)

I want a screenshot of gparted. You mean the partition isn't automatically mounted or? What error do you get and exactly when? Samba is for sharing files between different computers, you don't need that for this.

Your BIOS is not anywhere on your disk as far as I know but on a BIOS EEPROM chip on your mobo.[/QUOTE]

so if my bios isnt on my disk what is this 2.93gig space? its a fat32 that i assumed was part of system startup. its hda1.

as u can see have space free on my linux set up but i have no idea how to access them hda 8 n 9 have lots of space i can use

hda4 is the other fat32 and its mounted i can read and write to it but i can create a link to it when i try i get the second image.

---

### Post by glotz on 2006-06-16
Ah, you cannot create symlinks on a FAT32 disk. Not supported by file system.

I think you have a pretty weird partition scheme going on there. Any particular reason? When I was double booting, I had one partition for windows (NTFS), one for swap (SWAP) and all the rest on a (EXT3). I had another disk for sharing between OSes (FAT32). Now it's Linux all the way for me.

---

### Post by maddbaron on 2006-06-16
i thought i had to create one scheme for "/" and "/home" "/swap" and others can i repartition and not lose anything?

---

### Post by glotz on 2006-06-16
That's optional. I'm not sure if you can repartition *on the fly*...

---

### Post by maddbaron on 2006-06-16
darn, thanks for the help tho least i got some extra space.

---

### Post by sailor2001 on 2006-06-16
[QUOTE=maddbaron]thanks i deleted the cache got some space back couldnt delete any language files since there was only english from what i saw. 

here is my disk outlook the one highlighted hda4 is as u can see full of space. i'd want to make that my default music folder but i dont know how to change it so i can create a link since everytime i try i get an error even with sudo nautilus i can create files in there but not link them together. i even think when i clicked share after right clicking i installed samba...i dont even know what that is. anyway here is the image.

the 1st two parts r windows even tho the 1st part is only 3gig;s and i dont use it for anything i assume thats where my system bios is.[/QUOTE]
your hda4 is a virtual memory. This is MS's overflow from your RAM. It only need to be 1 1/2 times the size of your RAM

---


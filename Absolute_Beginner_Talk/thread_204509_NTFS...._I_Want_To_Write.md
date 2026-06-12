---
title: "NTFS.... I Want To Write"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-06-27
i have 3 HDD's in my PC...

one is for windows XP (NTFS)
one is for ubuntu (unknown file system (Default))
one is for Music & Video that i download...(NTFS)

is there any way that i can write to my NTFS (music & Video) HDD from ubuntu, when i try it says i have not got correct permissions.....

when i log in as root, i still do not have permissions.. ??? **Confused**

Thanks in advance

S2K

---

### Post by ubuntuuser on 2006-06-27
There is currently no built-in write support for NTFS. There are posibilities to do so, but they require some profound knowledge and the will to risk losing all the data on those drives. I don't know how stable and reliable it is. If you are not of the faint of heart you may want to look [here]("http://www.jankratochvil.net/project/captive/")

---

### Post by ubuntuuser on 2006-06-27
I just found a tutorial here on the forum: [http://ubuntuforums.org/showthread.php?t=142481]("http://ubuntuforums.org/showthread.php?t=142481")

---

### Post by mozetti on 2006-06-27
You run the risk of corrupting the whole partition if you decide to write to ntfs. My recommendation is to use Windows to convert the NTFS partition you want to access to FAT32.

---

### Post by shoot2kill on 2006-06-27
[QUOTE=mozetti]You run the risk of corrupting the whole partition if you decide to write to ntfs. My recommendation is to use Windows to convert the NTFS partition you want to access to FAT32.[/QUOTE]

can this be done without losing all of the data stored on the HDD, and how do i do this,....

also, can ubuntu write to FAT32 drive with no possibility of errors....

thanks again for help

---

### Post by mozetti on 2006-06-27
[QUOTE=shoot2kill]can this be done without losing all of the data stored on the HDD, and how do i do this,....

also, can ubuntu write to FAT32 drive with no possibility of errors....

thanks again for help[/QUOTE]

Yes, it can be done without losing the data. Use the Computer Management/Disk Management tool in Windows to convert it.

And yes, Linux can write to FAT32 with no possibility of errors.

---

### Post by shoot2kill on 2006-06-27
[QUOTE=mozetti]Yes, it can be done without losing the data. Use the Computer Management/Disk Management tool in Windows to convert it.

And yes, Linux can write to FAT32 with no possibility of errors.[/QUOTE]


thankyou very much, im at college now, but when i get home i will do it straight away... 

also, i am going to be putting the HDD in an external case, via USB, will ubuntu support this still... i know windoze does...

thankyou again

---

### Post by Thundercat on 2006-06-27
Ubuntu recognises my cameras memory cards connected via USB so I imagine it will see your HDD.

---

### Post by matrooswolf on 2006-06-27
[QUOTE=shoot2kill]
also, i am going to be putting the HDD in an external case, via USB, will ubuntu support this still... i know windoze does...
[/QUOTE]
Yes no problem, I have a usb harddisk, just connect it ...
I have about the same setup as you, and have my music on FAT32

(Btw: You could also put all your music on Linux and access it from windows with this driver: [http://www.fs-driver.org](http://www.fs-driver.org))

---

### Post by erniewinner on 2006-06-27
8) some people don't like it,  but xandros 4 has ntfs support. it will take a few months for a free version though...

---

### Post by bucho on 2006-06-27
I've been interested in adding ntfs write support to my installation and have come across the following:

[http://wiki.linux-ntfs.org/doku.php?id=ntfs-en#how_safe_is_the_ntfs_driver](http://wiki.linux-ntfs.org/doku.php?id=ntfs-en#how_safe_is_the_ntfs_driver)

This is with reference to the method posted above (here it is again just in case):

[http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)

I'm not saying it's foolproof, but it doesn't sound that dangerous to me (keep in mind, if your system is hosed ](*,) , you can't hold me responsible :p ).

Have fun!

---


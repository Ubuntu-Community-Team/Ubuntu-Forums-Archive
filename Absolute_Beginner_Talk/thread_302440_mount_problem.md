---
title: "mount problem"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by paripamano on 2006-11-18
HEllo,

I have already had the same problem for a time, but the replies stopped. 

I'm trying again.:confused: 

1. I have a fat32 partition, but i have only read permission, no writing. i have a lot of music files there, which i want to rename in a music editor (without terminal), but it does not work. _how do i reach both read/write access?_

2. is it possible to _rename filenames without terminal commands_, for example in juk, or other id3 tag program?

3. is there an application for _changing location without terminal commands_ for each and every music file, i want to move to other dir's?

thanks a lot for answering these questions!!

---

### Post by localuser on 2006-11-18
For all your questions, you can use the File Browser.

If you don't have File Browser under Applications | Accessories, you will need to add it to your menu system

6.06: Applications | Accessories | Alacarte
6.10: System | Preferences | Menu Layout

File Browser will be under Accessories.  Once added to the menu system, you will find its icon in Applications | Accessories

> **paripamano said:**
>  _how do i reach both read/write access?_In File Browser right click file and go to Permissions tab

> **paripamano said:**
>  2. is it possible to _rename filenames without terminal commands_, for example in juk, or other id3 tag program?
In File Browser right click file and rename

> **paripamano said:**
>  3. is there an application for _changing location without terminal commands_ for each and every music file, i want to move to other dir's?
In File Browser right click and copy then navigate to desired location then right click and paste

For all of these things, your life would be *greatly* enhanced if you were to learn how to use the terminal commands.

---

### Post by paripamano on 2006-11-18
i am learning!

but in the permission tab it says root, and i cant change it, because i am not the owner of the file. so cant rename it. how to make the whole partition write access, not in root only?

thnks

---

### Post by DOD1951 on 2006-11-18
Try this [http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by paripamano on 2006-11-18
i already read that and did the things written. the partition is mounted, but i still cannot have write access. what now???

---

### Post by DOD1951 on 2006-11-18
You will need to open the file browser as root to change the file persmissions so that you can have read/write access. I'm not sure how you open the file browser as root but bet there are heaps of people in here who do. They would also be able to explain how you do this through the terminal which I am sure would in the end be faster.

---

### Post by paripamano on 2006-11-18
thanks, so can anybody tell me how to access the file browser as root, and change the permission of that mounted partition for write access also, not only read, but no as a ROOT!?

pls help

---

### Post by CatKiller on 2006-11-18
> **paripamano said:**
> thanks, so can anybody tell me how to access the file browser as root,

```
gksudo nautilus
```

>  and change the permission of that mounted partition for write access also, not only read, but no as a ROOT!?

[http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows](http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows)

---

### Post by paripamano on 2006-11-19
thnks for any help, i did what you told me and read the things. 

i had this partition already mounted, but as i told only as a root and with only read access. as root in nautilus i couldn't change the owner to my name, so i did what i read in the wiki page you sent, but i unmounted the partition first, because i had it already mounted. is it okay to do it like that?- unmount it, before mounting again for read and write access?. 
- do i have to edit the fstab also, or is it enough what the wiki said and just write sudo mount /dev/hda1 etc...???

thnk

---

### Post by CatKiller on 2006-11-19
> **paripamano said:**
> is it okay to do it like that?- unmount it, before mounting again for read and write access?. 

I think that's what you're supposed to do.

> - do i have to edit the fstab also, or is it enough what the wiki said and just write sudo mount /dev/hda1 etc...???

It depends on whether you'd like it to mount every time you boot the computer. If you would, put the line in fstab. If you wouldn't, mount it manually each time. Intructions for each are in that guide.

---

### Post by Buck2348 on 2006-11-19
> **CatKiller said:**
> 
Code:

gksudo nautilus



CatKiller:  That's something I've been wanting to know for two weeks; thanks a lot.

Can someone tell me why I get the following every time I execute a gksudo command in terminal

```
(nautilus:10163): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

It seems to be no problem because the command goes through, but I'm curious.

Thanks,
Buck

---

### Post by CatKiller on 2006-11-19
> **Buck2348 said:**
> Can someone tell me why I get the following every time I execute a gksudo command in terminal

[https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917](https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917)

---

### Post by Buck2348 on 2006-11-19
Thanks once again, CatKiller.  Now I know the problem isn't peculiar to me.

Buck

---

### Post by paripamano on 2006-11-19
Thanks a lot for help. i did everything as it is written down. it seems i have read/write access. the owner is still root, but probably it has to be like that always.? 
one more thing: is it normal that it placed automatically a little red emblem on the folders in the partition, and its a lock (only readable). why is it there, if i can rename, move files etc.? i shouldn't bother?

---


---
title: "After using ubuntu, I am not able to access windows partition !"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by poseidon123 on 2006-01-26
Hi,

I am new to ubuntu :) and using it for the first time. Now when I booted into ubuntu, everything looked great and it also mounted my partitions automatically. Than I took a snap of the screen and saved it on the desktop and than by logging into root, I put it in /dev/hda5 which happens to be windows G: partition. 

Now when I went back to windows to get that image, **I was not able to open that partition drive at all !!!** It is asking me that "this disk in drive is not formatted,Do you want to format it" 

What can be done ? and why this happened ? how can I get my data back becuase if I formatted the partition than I will loose everything...

---

### Post by dueY on 2006-01-26
[QUOTE=poseidon123]Hi,

I am new to ubuntu :) and using it for the first time. Now when I booted into ubuntu, everything looked great and it also mounted my partitions automatically. Than I took a snap of the screen and saved it on the desktop and than by logging into root, I put it in /dev/hda5 which happens to be windows G: partition. 

Now when I went back to windows to get that image, **I was not able to open that partition drive at all !!!** It is asking me that "this disk in drive is not formatted,Do you want to format it" 

What can be done ? and why this happened ? how can I get my data back becuase if I formatted the partition than I will loose everything...[/QUOTE]


What was the file format of the partition in question?  You wrote to it from Linux, but can read from it in Windows, so I'm guessing FAT32?

---

### Post by Iowan on 2006-01-26
Perhaps another, more chilling question might be: What file format is it NOW?
I'm new enough that I don't know the Ubuntu version of MS FDISK (partd?)

---

### Post by dueY on 2006-01-26
[QUOTE=Iowan]Perhaps another, more chilling question might be: What file format is it NOW?
I'm new enough that I don't know the Ubuntu version of MS FDISK (partd?)[/QUOTE]

```
sudo fdisk -l
``` ?

---

### Post by dcast on 2006-01-26
why would you want to access windows anyway??? lol :)

---

### Post by spacetime on 2006-01-26
Oh dear, this does not sound good...

Did you copy it like so:

root@yourbox:~# cp image.png /media/hda5

or:

root@yourbox:~# cp image.png /dev/hda5

?

---

### Post by aysiu on 2006-01-26
[QUOTE=dcast]why would you want to access windows anyway??? lol :)[/QUOTE] To someone trying to access her Windows partition, this isn't funny, even if you put a smiley at the end.

---

### Post by hillbilly on 2006-01-26
Is this the first time that you loggin back into windows are setting up dual boot ?

---

### Post by poseidon123 on 2006-01-26
> What was the file format of the partition in question? 

Ya it's FAT32 and I am using Win XP

> What file format is it NOW?looks raw to me. while checking at admin toold -> computer management > disk defragmentar, it's not even showing that partition. I was having 6 partition, all FAT32 and it's only showing the other 5 now.

> root@yourbox:~# cp image.png /media/hda5

or:

root@yourbox:~# cp image.png /dev/hda5

**The second one - (I am just getting the feeling that I screwed UP!)**
All the mount partition folders were there on the desktop, and I tried to manually put the image into folder /dev/hda5 but it said you don't have permissions, so I opened console, and did in root mode
#cp image.jpg /dev/hda5 
Is directly putting image into this way caused the problem ?

> Is this the first time that you loggin back into windows are setting up dual boot ?
No, the second time. But this is the first time, I have put anything on the mounted partition

---

### Post by dueY on 2006-01-26
[QUOTE=poseidon123]Ya it's FAT32 and I am using Win XP

**The second one - (I am just getting the feeling that I screwed UP!)**[/QUOTE]

Not 100% sure but I think this indeed is where you screwed up.  You basically made your partition a screenshot?  You didn't copy the file to a directory within the partition, rather you copied the file to the actual partition as root thus overwriting it.  Maybe someone else can explain this better...

---

### Post by dueY on 2006-01-26
[QUOTE=poseidon123]Ya it's FAT32 and I am using Win XP

**The second one - (I am just getting the feeling that I screwed UP!)**[/QUOTE]

Not 100% sure but I think this indeed is where you screwed up.  You basically made your partition a screenshot?  You didn't copy the file to a directory within the partition, rather you copied the file to the actual partition as root thus overwriting it.  Maybe someone else can explain this better...

---

### Post by poseidon123 on 2006-01-27
Well sorry to bump it again, but I am still not sure what to do ? Can I still retrieve the information in the partition or is everything gone ?

---

### Post by dueY on 2006-01-27
[QUOTE=poseidon123]Well sorry to bump it again, but I am still not sure what to do ? Can I still retrieve the information in the partition or is everything gone ?[/QUOTE]

I guess you could try slaving it and using a data recovery program in Windows... not sure if that will work though.

---

### Post by poseidon123 on 2006-01-28
*sigh* I guess than I have to format the partition :(

Now can anyone tell me what is the proper way of copying to the mounted partitions in ubuntu ?

---

### Post by Herman on 2006-01-28
>  Now can anyone tell me what is the proper way of copying to the mounted partitions in ubuntu ? [UserDocumentation, the official Ubuntu Wiki.]("https://wiki.ubuntu.com/UserDocumentation")
Here's a link to the Wiki, which is a great place to look for information to help us all learn to do all kinds of things with Ubuntu. (Look under 'hard disks and partitions').
There is also the life preserver icon in the middle of our top panels of our desktops with the Ubuntu 5.10 Starter Guide, that's a great source of information too, so are the other links there in the Help Topics.
Also, there's aysiu's excellent .pdf document 'ubuntu_user_guide' if you can find where to download one of those, they are great! Aysiu's fourth signature link on his post on the previous page of this thread is about mounting Windows partitions too.
Also, there's this page [here]("http://users.bigpond.net.au/hermanzone/p10.htm"), (which can also be found by following aysiu's fifth signature link).
I hate reading about anyone having problems. I hope some of these information sources will be useful to you now and for lots of other things you might also want to do. Good luck and keep smiling, :-D (Herman)

---

### Post by Herman on 2006-01-28
> *sigh* I guess than I have to format the partition :sad: Before you do that, you might like to wait a while and give it a little 'cooling off period', don't rush in and format things yet if there is anything on it you can't re-install easily. 
Have you tried mounting the partition with a live CD to see for sure if everything is really all gone? (Herman)

---


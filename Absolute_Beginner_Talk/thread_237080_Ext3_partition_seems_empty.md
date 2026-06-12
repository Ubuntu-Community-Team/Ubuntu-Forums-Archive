---
title: "Ext3 partition seems empty"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by timmeeej on 2006-08-15
Hi! I had an Ext2 partition which I mounted on /home. Then i tried converting it to Ext3 using Gparted. Gparted advised me to reboot, after that i changed my fstab to ext3. The new Ext3 partition mounts just fine, the only problem is.. it's empty.. 

](*,) 

The weird thing is, Gparted says theres 1.27 GB of used space on my home partition, so that must be my lost files. I've included a screenshot of Gparted. Is there a way to get my files back?

Thanks. (Please excuse my bad spelling and grammar)

Fstab:
/dev/sda4       /home               ext3    defaults 0       0

---

### Post by lamego on 2006-08-15
Try checking it with e2fsck .

---

### Post by ComplexNumber on 2006-08-15
[B]timmeeej
[/B]i'm slightly confused (not least because that screenshot is in german) - there's a few pieces missing from the jigsaw that may allow someone to find the problem. did you unmount the partion that you converted to ext3 before you converted it? i hope so (then again, i wouldn't have thought it would allow you to do otherwise)

is you lost partion still called '/home'? if not, thats probably the problem. 
i did an install about a month ago. i had my partitions all set up, so all i needed to do was install the packages. buit stupid me forgot to assign the mount point of '/home' to my intended home partition that held all my files and settings from the previous install. consequently, my home directory ended up on the root partition whilst my previous home directory was stuck on my previous /home partition. i just did a reinstall and made sure that i assigned the /home mount point to my /home partition...and all was well.


also, does your desktop look exactly the same as before you converted it to ext3? and are you executing gparted from the live cd?

---

### Post by timmeeej on 2006-08-16
Yes, I unmounted my Ext2 before convering. GParted gives an error if you don't. 

My lost partition is still called /home. The only thing it contains right now is a folder called "Lost&Found". I have checked for hidden files.

My desktop doesn't look exactly the same as before, you can't login if you don't have a home directory. (I'm logged in as root now :-$)

ps. The screenshot is not in German, it's Dutch ;)But you were close. Should I change my langauge settings to English and post another screenshot, or can you figure this one out.

I'll give e2fsck a try. Thanks

---

### Post by ComplexNumber on 2006-08-16
> 
My desktop doesn't look exactly the same as before, you can't login if you don't have a home directory.
yes, i know. thats because the system creates a new home directory on the root partition. thats what happened to me.


> 
My lost partition is still called /home.
are you sure thats not just the label for the partition rather than the mount point? during my trials and tribulations the other month, i had an emplty partition called home1 and another called home. it just seems to be the label, but isn't indicative of the mount point.

> The screenshot is not in German, it's Dutch
there goes my hopes of becoming a dutch language  teacher :p. oh well, they're both germanic anyway (same as english).


> 
or can you figure this one out.
well, provided that babelfish can give me a few clues.

---


---
title: "unable to boot mac osx !!"
date: 2008-03-18
forum: Apple Intel Users
---

### Post by johansto on 2008-03-18
hey guys

well i feel kind of stupid, i installed ubuntu with bootcamp on my imac without knowing anything about linux.

it works ok only that : now i can't boot mac osx !! 

when i press alt when computer is starting, i only get one choice, "windows" (which is actually ubuntu)

i have tried with rEFIt from bootable cd, but osx never comes up as an option !

i really don't know what to do now and i could absolutely use some help !!! plus i can't access all my files on the mac partition (even though they're still there) and feel really handicapped.

please help ?
anything, just let me know what you think...

cheers,
johan

---

### Post by LeoSolaris on 2008-03-18
I did this when I first installed Ubuntu...

The partitioning ability in the regular install is a destructive partitioning. What you did was just cut OSX down without moving any of the data off the part you just cut out... meaning it's dead. Sorta like cropping a photo verses shrinking it. Same Idea, the part cropped is lost from the overall picture, but the shrank one has the full picture, just smaller.

Reinstall OSX, then when you go to reinstall Ubuntu, go through the Menu->System->Administration->Gparted (in the LiveCD).   Use Gparted to repartition the OSX. It will take longer, but what it is doing is moving any information scattered over the whole disk down to a smaller part of the disk. The one in the installer doesn't do this for some reason, it just axes anything on the disc that is in the way. (Ubuntu is still improving and growing!)

I really hope that you made a backup of your personal data before you installed Ubuntu, otherwise, your kinda SOL. A Tech professional might be able to recover the partially erased OSX, but I doubt it.

Sorry bout the bad news, and I hope this doesn't sour you on Ubuntu.

(If anyone knows a better way, please speak up! This was the only thing I could do when I did this to XP, and theoretically it's the same thing, just a different OS.) 

Leo

---

### Post by johansto on 2008-03-18
wow...that kind of sucks...

the thing is, the mac partition doesn't seem to be destroyed. only the personal files are denied of access (documents, music pictures etc) but the files i created are accessible, and i can copy stuff from it. 
isn't there any way i can have access to all my files ?

otherwise i guess i'll be crying over all my stuff, havn't made any backup for quite some time now.....

but thanks for the tips !

johan

---

### Post by cyberdork33 on 2008-03-18
boot from the OS X dvd and repair.

You can still get your files. They have permissions accessible only to a different user, so you can only access them as root.

I am suprised that you say the partition is still there. I would have guessed that you just formatted over it.

Since you used bootcamp, OS X resized it's own partition and it should have been fine... but if you did not install to the newly created partition, then you probably messed something up.

---

### Post by LeoSolaris on 2008-03-19
I hope he got that message. I had assumed that he did a destructive partition, rather than one that just locked him out of personal folders! This is why it is hard to give tech support over the net, or over the phone...can't always tell what's happening.

I hope my erroneous advice doesn't cause too much damage.

Sorry bout that!
Leo

---

### Post by cevans on 2008-03-19
> **LeoSolaris said:**
> I hope he got that message. I had assumed that he did a destructive partition, rather than one that just locked him out of personal folders! This is why it is hard to give tech support over the net, or over the phone...can't always tell what's happening.

I hope my erroneous advice doesn't cause too much damage.

Sorry bout that!
Leo

Luckily, it's possible that by following your advice, he will fix OS X and not lose his data, as long as he doesn't tell the installer to format the drive - I don't believe it's the default, at least with Leopard.

My advice would be to either repair or reinstall OS X using the Archive and Install method. It really doesn't sound like the partition has been partially overwritten, as I don't see how it could possibly be mounted in any normal way if that were the case.

And as a note to johansto:

**I'm almost certain that you did not overwrite your OS X partition, and you have almost certainly not lost any data!**

---

### Post by johansto on 2008-03-19
i got the message don't worry leo !

i've tried booting with osx cd, but couldn't get it to "repair". actually, it doesn't even recognise the mac partition, but only boot camp and linux !

but with the disk utility and can make a disk image of the entire HD. do you guys think that could work, considering it doesn't see the mac partition ? anyways, i have to find a external HD of over 300gb which i don't have....

but i'd like to thank you for your quick replies, really, i love the "community" solidarity of linux users ! so thanks !

johan

---


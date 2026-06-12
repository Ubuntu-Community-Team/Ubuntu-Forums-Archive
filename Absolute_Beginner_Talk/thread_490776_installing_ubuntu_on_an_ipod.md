---
title: "installing ubuntu on an ipod"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-07-02
hello all,

once upon a time i was bored and pondering what else i could possibly do with linux.then it occured to me i had a last gen perfectly functionall ipod sitting on my desk!! so naturally i plugged it in to my xp pc put 'er in disk mode and restarted into a kubuntu live cd. my ipod was detected succesfully and it appeared to have installed correctly!! but to my surprise i restarted my laptop with my ipod plugged in and my comp stalled at "loading one time boot menu" phase of its bios!! argh!!!

so yea long  story short, anybody have any experince using an ipod as an externall hdd to run linux off of?

any help appreciated ty

jv

---

### Post by p_quarles on 2007-07-02
Not sure what you're attempting to do. There are ways of using a live CD and an external storage device to create a persistent Linux system, but using an iPod for this sounds like kind of a waste (=a 40 GB external drive costs a lot less than a 40 GB iPod). 

I know of some resources that might help if you explain a little more. If you want Linux firmware for the iPod, I think Rockbox might work (I can't remember). If you're trying to run Linux with a USB drive, there are tutorials out there about how to do this.

---

### Post by Rocket2DMn on 2007-07-02
> **gameman12 said:**
> 
once upon a time i was bored and pondering what else i could possibly do with linux.then it occured to me i had a last gen perfectly functionall ipod sitting on my desk!! so naturally i plugged it in to my xp pc put 'er in disk mode and restarted into a kubuntu live cd. my ipod was detected succesfully and it appeared to have installed correctly!! but to my surprise i restarted my laptop with my ipod plugged in and my comp stalled at "loading one time boot menu" phase of its bios!! argh!!!

You have entirely too much time on your hands, my friend.  Sounds like you may need to set your BIOS to read the USB as the primary boot device (not the HDD).  If you think Kubuntu installed correctly, fiddle with that and then fill us in.

---

### Post by Raineer on 2007-07-02
Don't think Ubuntu is the right choice. I am a long-time Rockbox user, but that isn't Linux either. You want to use [iPodLinux]("http://ipodlinux.org/Main_Page").

---

### Post by gameman12 on 2007-07-03
sry everybody but i didn't give too much info. first off, its an extra ipod and i don't use it, second i have my normal ubuntu install on an externall hdd, thrid, i know i have too much time on my hands, forth i am trying to use the ipod as the externall hdd, so i'm thinking the problem is with something on the ipod and my bios isn't liking it, i'm gonna keep fiddling,

thx

---

### Post by Rocket2DMn on 2007-07-03
Perhaps the ipod needs to be reconfigured to recognize it has a bootable partition.  Does it even let you partition it and give it a swap partition and all that jazz?

---

### Post by gameman12 on 2007-07-03
yea it does, i tried putting grub on my pc's hdd too and it fried cause the ipod wasn't recognized as bootable evidently....so i had to restore the mbr

---


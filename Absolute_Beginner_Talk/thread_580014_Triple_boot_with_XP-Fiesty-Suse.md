---
title: "Triple boot with XP-Fiesty-Suse"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by new2Forum on 2007-10-18
This isnt really a ubuntu install question as I already have XP and ubuntu installed and running.  I now have to add Open suse as well for school purposes.  I started the install and it aborted due to an error.  I am glad as it prolly would of taken over my drive.

Does anyone know how to install Suse as my third boot option?
Ubuntu was easy as it had the partition options during the install.

Any help would be greatly appreciated.

---

### Post by stijngysemans on 2007-10-18
What you maybe can do is boot up ubuntu and start the program "gparted" . Prepare yourself an empty partition (or two, for the swap), where you can install open suse on.

If you can't find this program in you applications menu, search for in using th add/remove programs tool!

---

### Post by Duck2006 on 2007-10-18
> or two, for the swap

Same swap partition will do suse and ubuntu so you only need one partition for the suse / "root" partition. and yes use the live cd of gparted to partition the hard drive for the new partition and then install and have fun.

---

### Post by Gio-van-I on 2007-10-18
> **new2Forum said:**
> This isnt really a ubuntu install question as I already have XP and ubuntu installed and running.  I now have to add Open suse as well for school purposes.  I started the install and it aborted due to an error.  I am glad as it prolly would of taken over my drive.

Does anyone know how to install Suse as my third boot option?
Ubuntu was easy as it had the partition options during the install.

Any help would be greatly appreciated.

It would be nice to know what error you received.
One thing I can tell you is that triple booting on a single hard drive is possible, but has a downside.
You can only create 4 primary partitions on a hard drive. Linux uses 2: 1 for /, 1 for swap. Windows needs only 1.
I assume different linux versions can use the same swap, So for a triple boot you will need 1 swap, 2 linux and 1 windows primary partition.
The downside I was talking about is that you usealy have an extended partition as wel. You use this for creating an array of loose partitions without a limit in their number. But it uses a primary partition slot. So if you have an extended partition you'll only be able to dual boot.
Looking at your story I think this is the problem you encountered.
If so you can solve this by:
-Getting rid of your extended partitions (beware to store the data on it first!)
-Deviding your OS's on multiple drives (a basic grub manual will guide you through how to set your settings to boot from an other drive)

I hope you have some use for this information.
If you want a better answer, Please post the errors and hardware you are using. Knowing how old the motherboard is and how large your HD is could help to prevent boot isseus.

Good luck!


Edited:
Just seen a disc layout with use of extended partition for linux and swap...
I guess I've been out of the game for to long. That or they tought me wrong during my education...
Still hope you have use for all I told. Good luck.

---

### Post by new2Forum on 2007-10-18
Thanxs for the responses everyone,

My system is an AMD 3800 Athalon X2 64   It is about a year old.  The harddrive is 250gb.  I currently have 40gb of that reserved for ubuntu.  I am a newb to this if that isnt already apparent, :). 

The error that I recieved was to doo with the reposititories, I think it tried to access the web for them and wasnt able to, this was due to the fact that I booted with the Open Suse 10.3 disc.

I think you are right and I prolly do have an extended partition.  I am getting an external 80gb tomorrow, I am thinking that it might be easier to install on that, rather than mess with the extended partition.

---

### Post by Duck2006 on 2007-10-18
> So if you have an extended partition you'll only be able to dual boot

Not true. The only OS on the drive that needs a primary partition on the drive is windoze. A linux os system will boot very happyly fron an extended partition.

---

### Post by new2Forum on 2007-10-18
Another alternative, that I think will be the easiest is to use VMware with an Image of susie.  That way no install is needed and it is only 800mb.  
Thanxs for the quick replies, this forum is most definitely an excellent source of information.

---

### Post by rickggreen on 2007-10-18
There is a great site to help with dual booting.

Illustrated Dual Boot Site

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

And this one also

[http://www.psychocats.net/](http://www.psychocats.net/)


"Must have" sites for newbs, besure to bookmark them.

---


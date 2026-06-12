---
title: "Help!!!"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by avgjoe22 on 2006-11-26
Okay... I'm freaking out right now.

So... I installed Ubuntu on my system, and that was cool at first, but then I realized that it wiped like 5 of my partitions!

Then, I used this "System Recovery" CD boot thingy, and now when I boot up it says some **** like "GRUB Failed to Load" and "Error 17"

OMFG!

I really need my Windows!  I have so many files on there...

And my whole intent of using UBUNTU was to SAVE files!!!

Help!

(And please, don't flame me, I realize it's 100% my fault...)

](*,)

---

### Post by shin on 2006-11-26
Huh. Nice one. Btw change the name of this post because 'help' isnt that descriptive. Now what was that System Recovery CD? Windows CD or what?

You wrote that Ubuntu wiped out 5 of your partitions. You mean your whole hdd? If Ubuntu removed your windows partition and installed over it after formatting it to new fs then there's not much you can do but to try to recover whatever you can. Get a hold of some good data recovery software, install it (not on this hard drive) and pray.

But if it didnt install over your windows partitions and just wiped out information about it - then your files should still be there unharmed. You just need to restore partition table.

How to do it - no idea, never tried. 

Good luck though.

---

### Post by Derek Tomes on 2006-11-26
I would recommend two things:
 
1. Don't do anything else to your computer
 
2. Get the person you most trust who knows a lot about computers, and ask them to help you. Offer to pay them if you must.
 
It is often possible to recover information from drives/partitions that have been accidentally deleted. However, every mistake you make from this point will only make it harder to recover the data. In fact, every time your comouter starts writing stuff to your HDD, you make it less likely you will get the data back.

---

### Post by avgjoe22 on 2006-11-26
Sorry, I was a bit flustered.

I'm a little calmer now.

I had two Windows XP installments cause I have two hard drives.

The automatic partitioner thingy in Ubuntu left my main windows alone, and used up either all of my remaining partitions, or all but one - i never figured it out because there were two partitions in my remaining windows - "C:\" and "Disk" - but I couldn't understand what was in the "Disk" partition.

My other windows got wiped out.  Cool - I didn't use it anyways.  My other partitions were housing some big programs - Netbeans, Autocad, Photoshop, and 3D Canvas to name a few...  "But I can reinstall them after I figure this out" I thought.

Nope.

Ubunbtu took the liberty of soaking up 120 GIGABYTES of space...  How much did it use?  THREE.  So I used that system recovery thing and tried my luck.

See my other post [HERE]("http://computerforums.org/showthread.php?t=47678").

I don't remember what *exactly* I did...

But I'm pretty sure though that I resized the Linux Partition and used the massive leftover space to create a new NTFS partition, which I could use for my big programs, music, videos, etc.

Does anyone have any ideas on how to fix the "Error 17"?

---

### Post by turbojugend_gr on 2006-11-26
Calm down, and do not rush anything. You have to avoid consecutive wrong decisions.

Here's is waht I would do. I would put my ubuntu Live CD (also known as Desktop CD). I would let it boot. When I was in my LiveCD environment, I would open a terminal. Note we won't write anything to your disk, so do not panic, we will only make sure if the date is still there.

In that terminal let's type: "sudo mount -r -t ntfs /dev/sda1 /winxp"

Note that you need to change sda1 to your ntfs partition (sda1 --> "s" stands for a sata disk,if it is an ide disk then replace it with "h"//"d" indicates that's a drive so obviously leave it as it is// "a" stands for 1st disk, if it is the second change that with "b" and so on//"1" indiciates it is the first partition on that disk, if it is the second put 2 there and so on//// e.g: if your windows partition is on the 3rd partition on your second IDE disk then "sda1" should be "hdb3").

When you have succesfully mounted windows partition (that would be if no error message appear), then in type "cd /winxp" (that is used to navigate to that partition, since /winxp is where we mounted it) and then "ls -a" (to list the contents). If all your files appear then you are OK. You can smile, nothing disasterous happened. If nothing familiar appears, then before breaking your PC out of anger, plz post here your Partition table (in other words, post how many disk you have and which partition is windows on, so we can help you).

I hope nothing is erased, awaitng your reply, TJ.

---

### Post by turbojugend_gr on 2006-11-26
SO I guess, you have all your valuable data there. IF yes folow [this]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by avgjoe22 on 2006-11-26
Okay, I didn't know what was what at first, but I went to System>Administration>Disks and found my Windows (I think) - it says:

Device: /dev/hdb6
Filesystem: Windows NTFS
Access Path: /tmp/disks-conf-hdb6
Size: 9.41 GiB (7.66 GiB Free) <<That's what windows was before i messed with anything.
Status: Accessible [Disable] [Browse]

BUT when I type:  sudo mount -r -t ntfs /dev/hdb6 /winxp

it says:  mount: mount point /winxp does not exist

](*,) 

What now?

---

### Post by shin on 2006-11-26
Create the mountpoint

```
sudo mkdir /winxp
```

About grub error - you need to restore grub as turbojugend_gr said.
Instructions are on [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)
But firstly check what exactly happened with data and your partitions with livecd. If that's possible - backup anything you may need later before taking any further actions.

---

### Post by turbojugend_gr on 2006-11-26
> **avgjoe22 said:**
> Okay, I didn't know what was what at first, but I went to System>Administration>Disks and found my Windows (I think) - it says:

Device: /dev/hdb6
Filesystem: Windows NTFS
Access Path: /tmp/disks-conf-hdb6
Size: 9.41 GiB (7.66 GiB Free) <<That's what windows was before i messed with anything.
Status: Accessible [Disable] [Browse]

BUT when I type:  sudo mount -r -t ntfs /dev/hdb6 /winxp

it says:  mount: mount point /winxp does not exist

](*,) 

What now?

Do as shin suggested "sudo mkdir /winxp". You get that error cause /winxp folder don't exist. THe previous command will create it. Keep following my previous instructions on checking if your windows data is still there. If everything is there, follow the guide we suggested to get your GRUB back.

BTW, it is perfectly logical took your whole drive and just installed 3gigs. You told it to use the whole drive and it just did so, since 3 gigs was the installation, the rest are free as they should.

---

### Post by avgjoe22 on 2006-11-26
I'm trying to fix it, I may have it...

I'll keep everyone posted as 2 years of work hangs in the balance...

(Dramatic Overture...)

---

### Post by jerrykenny on 2006-11-26
Stick with TURBO, thats good advice he's giving you . . . good luck

---


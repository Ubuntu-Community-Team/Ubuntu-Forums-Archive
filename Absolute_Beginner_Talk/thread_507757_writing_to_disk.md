---
title: "writing to disk"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by ablot on 2007-07-23
Please can someone advise me.

I'm installing ubuntu onto my laptop ... when it gets to "partitioning the disk" page it offers me guided partitioning ... so to make life simple I choose the first option which resizes hda1 and other stuff ... the partition size stands at 59% (18gb's) which is fine by me ... so I press continue.

I then get a screen which says that any changes must be written to disk ... I have the option to continue or go back. I click continue and after a few seconds the machine freezes.

So my question is ... what do I have to do to make it work? Should I write the changes to disk? what are the changes ... 59%? How do I write the changes to disk?

...hmm ... thats three questions!

... Well ... can anyone help me? ... Please.

---

### Post by gn2 on 2007-07-23
Are you attempting to create a dual boot, or is the hard drive empty?

If you're trying to shrink an NTFS partition to create room for Ubuntu, the partitioner isn't always able to move data out of the way.
Disk Defragmenter can show if there's data where you want to install Ubuntu, if there is you will probably need to shift it with a Windows compatible partitioning tool.

---

### Post by Foxmike on 2007-07-23
Hi and welcome to Ubuntu!:)
 
Pressing to continue will write the changes to disk.  What happens, is that on the first screen you select what you want to do and in the second, you just confirm that this is what you really want to do.
 
Creating partitions can take time, but not so much.  Try it again to see if it really freezes (if nothing moves after, say, 6-7 minutes, I would say it is frozen).  If it freezes, I would first check the integrety of the disk.  You can do so by the very first menu you get when you boot and from wich you usually select "Install" or something like this.  If the integrety is good, I would re-begin the install, but them I would choose the manual partitionner.
 
Good luck!:)

---

### Post by ablot on 2007-07-23
I have checked the disk in the usual way and it is good.

... But I think I've done a silly thing! I decided that it might be simpler to just install onto the whole computer - to just overwrite windows.

... I got as far as it telling me it was installing ubuntu. It got to 15% installation then froze.
I tried it again ... and it froze again at the same place.
Unfortunately the laptop now has no windows (which is great) ... but no ubuntu either.

So ... what happens now?

I feel confident that ubuntu will be loaded ... but I think I need help.

---

### Post by ReaderRat on 2007-07-23
Download a copy of this:  [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)
And burn the iso image at a slooow speed. Then use it to clear & repartition your hard drive.


IF you have no way to do this, then use your Win XP disk and let it go to the point of installation where you can delete all partitions and do so. Remove the disk and restart with the computer with the LiveCD.

---

### Post by e_james on 2007-07-23
Some motherboards have a bios option which protects the computer from virus activity by attempting to prevent writing to the hard drive boot sector. I assume this is not a factor.

I have used the live CD to set partitions to my preference but I have never used it for install. I use the alternate CD instead. With Dapper it was sometimes necessary to use the boot options "noapi nolapi acpi=off" in order to avoid a hang during install. So far I have not needed to use these with Feisty.

---

### Post by ablot on 2007-07-24
... I wouldn't asume anything here.

So how do I check to see if there is a bios option?
How do I actually get to the bios bit?
What do I do if I find the bios option?

---

### Post by ablot on 2007-07-24
Ive downloaded Gnome PART onto my windows machine ... do I simply put it onto a CD then load it onto the laptop (which has no working system) ... or do I have to open it in windows THEN load it onto a CD?

---

### Post by Foxmike on 2007-07-24
Look, you can just boot the Ubuntu live CD.  On it there is gparted, you can access it via the menus: System -> Administration -> Gnome Partition Editor.  Thru it, you wiill be able to resize/remove/add partitions manually.

---

### Post by ablot on 2007-07-24
Thats great news!
When I get there I believe I will need to have three partitions (hda1, swap, and something else ... I don't need anything for windows) ... what would you suggest for a 33gb laptop?

---

### Post by Foxmike on 2007-07-24
It depends on your RAM.  Generally, if you have a 512Mb+ RAM, you need the amount of RAM for the SWAP partition.  If less, calculate about twice your RAM.  For the root partition ("/"), I would suggest 6-7 Gb.  Unless you install LOT of things (GNOME+KDE+a lot), you would end up filling about 6Gb.
 
Keep the remaining for a /home partition.  I like to keep a separate /home partition in order to keep personnal things separate.  Matter of taste.

---

### Post by ablot on 2007-07-24
Something similar has been suggested to me.

However, I get a bit stuck when I use the manual partition. No one seems to be able to tell me what the partitions are ... ie primary or secondry ... ext2, ext3, or what ... 

So I guessed:
Root 10gb primary ext3 I use "/"
Swap 512mb primary Linux swap 
The rest is about 27gb primary ext2 I use "/home"

... May I say that I think the problem lies somewhere else ... the point at which the computer freezes is at the point where ubuntu is "detecting file systems" ... that sounds like a problem before it gets to the partitions ... but I could be wrong.

So ... where do I go from here? I'm not giving up on this ... I only hope that the forum does not give up on me.

---

### Post by Foxmike on 2007-07-24
What you have guessed is right.  Generally, hard disks only allow 4 promary partitions (hda1-4).  If you need more, you can build-up an extended partition in which you build secondary partitions (hda5-16).  Now, your root (/) (and more precisely your boot (/boot) partition if it is separate, which is not the default) need to be on a primary partition, as well as the swap partition.  Everything else can be on a secondary partition.
 
Now, maybe you should try manually partition your hard disk using gparted **before** to start the install, and then just use those pre-created partitions in the install.

---

### Post by ablot on 2007-07-24
... I have just tried loading MEPIS ... it worked a dream - no problems.

Thanks for all your help.

---


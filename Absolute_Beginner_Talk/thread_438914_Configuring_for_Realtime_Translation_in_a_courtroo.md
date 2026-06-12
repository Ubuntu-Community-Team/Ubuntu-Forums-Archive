---
title: "Configuring for Realtime Translation in a courtroom"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by jamillikan on 2007-05-10
I'd like to shrink ext3 down to allow a new partition 1 GIG in size and format that partition in FAT32.  I'd like to mount that partition in /home/jamillikan/ as "ASG" in order for my particular software to be able to output realtime to that partition which I'd then like to share using SMB with Windows clients so they can view the realtime proceedings.

I currently do this with Xandros 3.0 Business Deluxe, but I'd like completely to abandon Xandros in favor of Ubuntu.  (I'm using Edgy Eft).  I currently use Ubuntu with Gnome everywhere except in the courtroom and this would be the final step to abolish the Xandros distro entirely.  (Not that it's bad, I'm just over it.)  Ubuntu is so much better for me.  I just love it.

If anyone reading this knows how I can easily accomplish this without completely wiping out my current installation of Ubuntu and starting over, I'd appreciate any tips/advice/how-to you could provide.

Thanks in advance,

Joe

---

### Post by starcraft.man on 2007-05-10
You can use the [GParted]("http://gparted.sourceforge.net/livecd.php") live CD to boot into a partitioner and resize any drive you like, then make a one GB partition. To minimize errors, its best to do one step at a time, so resize then apply that, then make the 1 GB and make that.

That should be it, do remember you'll have to mount it once your done :)

---

### Post by ikonia on 2007-05-10
questions 

1.) why do you want to format it fat32 ?
2.) What is mounting it "ASG" ?

you can't shrink a parition you'll have to destory and re-create or use a resize tool and hope there are no issues.

---

### Post by sc30317 on 2007-05-10
I think he means shrink = resize smaller

---

### Post by jamillikan on 2007-05-10
Because I'm using DOSEMU and my realtime output CAT software doesn't work unless I have a FAT32 partition mounted in DOSEMU.  ASG is just an arbitrary name I chose.  I could be E, F, G, whatever.

Hope this helps!

Joe

---

### Post by starcraft.man on 2007-05-10
Edit: hehe, he answered... anyway try the gparted live cd, should do the trick.

---

### Post by ikonia on 2007-05-10
if your mounting via samba - which you are, the native file system won't matter. 

If your mounting locally - then of course it will matter.

---

### Post by jamillikan on 2007-05-10
> **starcraft.man said:**
> You can use the [GParted]("http://gparted.sourceforge.net/livecd.php") live CD to boot into a partitioner and resize any drive you like, then make a one GB partition. To minimize errors, its best to do one step at a time, so resize then apply that, then make the 1 GB and make that.

That should be it, do remember you'll have to mount it once your done :)

I'll try your suggestion.  Thanks for your help!

Joe

---


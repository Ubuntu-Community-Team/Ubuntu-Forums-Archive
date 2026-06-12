---
title: "Removing Windows"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by LDRoamer on 2007-03-28
I have dual boot configuration with WinXP and Edgy. I would like to get rid of WinXP and just use Ubuntu on that machine. My hard disk is partitioned into two with WinXP on one partition and Ubuntu on the other. In the windows world WinXP is on the C drive and Ubuntu on the D. Just wondering if there is an easy way to get rid of Windows and use that partition as additional space for my Ubuntu installation. If there is a pointer to a how to somewhere that would be great.

Thanks.

---

### Post by martinw89 on 2007-03-28
You can use GParted to delete the XP partition and then expand the Ubuntu partition to fill the space.  You can find GParted in Synaptic.

Have fun  without Windows :)

---

### Post by seshomaru samma on 2007-03-28
after you format windows you will need to mount the new partition you created
read [this]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by LDRoamer on 2007-03-28
So it looks like there are two methods? One is using Gparted to delete the Windows partition add the space it to the Ubuntu one (leaving my hard disk as one larger partition) or I can format the existing partition and mount it using the tutorial supplied. Will I have any problems booting after I do either or will Grub still work?

---

### Post by nixclusive on 2007-03-28
Nope. you should not have any problems after that anyway. btw I'd really recommend the second option - format and mount - leaves little possibility for fs corruption. ;-)

---

### Post by martinw89 on 2007-03-29
Yeah, actually I agree with the others, the way I mentioned works but there's is safer.  Plus, the way Linux handles partitions is pretty much seamless, no need to worry about drive letters or anything like that.

---

### Post by Doug11 on 2007-03-29
Don't quote me on this , but you may have to a Live cd of GParted. I remember I tried to do that very thing not verylong ago, wipe out my windows partition to use it as a Ubuntu storage partition and I had to use the Live CD of GParted. If I just ran gparted from within Ubuntu, it would not let me edit any of the partitions, unless the newer versions will.

---

### Post by martinw89 on 2007-03-29
As long as the partitions aren't mounted GParted should be able to work with them.  So that means, within your installation, you would not be able to make any changes on your root partition.  But the LiveCD is definitely the way to go, and yeah GParted is on the Edgy LiveCD (not Feisty beta though, and I have no idea about earlier Ubuntus)

---

### Post by LDRoamer on 2007-03-29
Thanks for the help. i have the live CD for Edgy and I have the live CD for Gparted so I guess I am good to go. I will just reformat the Windows partition and then mount it. Sounds simply and pretty safe.

Thanks again. The help here is great.

---

### Post by Error47 on 2007-03-29
I wanted to do the same exact thing, I used gparted to format my windows partition to ext3. Then mounted that drive, and it worked.

---


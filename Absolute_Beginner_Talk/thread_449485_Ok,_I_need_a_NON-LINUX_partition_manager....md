---
title: "Ok, I need a NON-LINUX partition manager..."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Moleboy on 2007-05-20
The Linux manager just DOESN'T work for me, no matter how I change my partitions there is an error for it...does anyone know another partition manager?

Please don't just tell me to use the Linux one, I can't change any partition to any amount without some error...I've used the Linux one before with no trouble, can someone explain this please?

Thanks in Advance!

--Moleboy

---

### Post by starcraft.man on 2007-05-20
> **Moleboy said:**
> The Linux manager just DOESN'T work for me, no matter how I change my partitions there is an error for it...does anyone know another partition manager?

Please don't just tell me to use the Linux one, I can't change any partition to any amount without some error...I've used the Linux one before with no trouble, can someone explain this please?

Thanks in Advance!

--Moleboy

What error do you get? If you tell us more we can figure out why gparted isn't working (I assume thats the one your using). I don't think you will find another that works any better than GParted, I've used a few and it is quite good. I could recommend other programs for partitioning, but most of them that I know are windows based and paid for (acronis for instance, I had gotten a copy of that some months before I started using linux). Not many people are interested in making a free partitioner...

---

### Post by Wim Sturkenboom on 2007-05-20
partition magic
ranish partition manager

And maybe, if you post the error messages, someone can indeed say what's wrong.

---

### Post by Moleboy on 2007-05-20
Ummm, when I only try to do a little at a time it says,

File size too big.

this next one just makes no sense...

Sorry, there was an error and we can't complete the action.

Now, I've had linux before, and Ubuntu 7.04 before...and this has NEVER happened before...can someone explain it please?

Also, I need a free partition manager...partition magic isn't free I believe T_T

---

### Post by BHelts on 2007-05-20
[Ultimte Boot CD]("http://ultimatebootcd.com") has several partition utilities.

---

### Post by ugm6hr on 2007-05-20
Unusual to ask for a non-linux application on a linux forum...  

Sorry, but I haven't heard of any free Windows-based partition managers.  If you already have Linux ext2/3 partitions on the drive, I'm not sure that any Windows application would be able to resize those partitions anyway.  You haven't given much detail about your current HD setup, but I suspect that the problem is not actually related to the partition manager, but is actually an issue with your current partitions (i.e. their size, how full they are, maximum size of individual files, degree of fragmentation, the difference between free and used space etc).  You haven't mentioned which version of the "Linux manager" you used either.

If you are prepared to try again, I would suggest you defragment all your partitions in Windows prior to trying to resize / move them.  Then boot from the GParted Live CD (which has the most up-to-date GParted), and try to edit partitions in that (use the second boot option when it loads).

If that's wasted your time again - apologies.  But in that case, you may run into the same problems whichever partition manager you chose to use.

GParted - available from:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

PS: Don't forget to back-up prior to attempting.  Perhaps removing any large files from the HD prior to repartitioning may help the situation?

---

### Post by Salpiche on 2007-05-20
Can you post a screen shot of the entire error as well as the partitioning scheme? I have had several errors with partitioners but never with gparted.

---

### Post by Moleboy on 2007-05-20
ummmm...how do I take a screen shot? If you can tell me, I gladly will...

---

### Post by STREETURCHINE on 2007-05-20
application>accessories>take screenshot.

should do it

---

### Post by Jose Catre-Vandis on 2007-05-20
In line with the OP, when I try to use gparted from the live cd or from an installation (obviously not on the booted partition!), I also tend to get errors, so now I always use the gparted live cd, which always works :-) I know some of the commercial products will work on partitions from within Windows, but this seems a risky way of reorganising your filesystems.

---

### Post by STREETURCHINE on 2007-05-21
> **Jose Catre-Vandis said:**
> In line with the OP, when I try to use gparted from the live cd or from an installation (obviously not on the booted partition!), I also tend to get errors, so now I always use the gparted live cd, which always works :-) I know some of the commercial products will work on partitions from within Windows, but this seems a risky way of reorganising your filesystems.

yes i agree i seem to have trouble with gparted on the live ubuntu disk ,so i use the live gparted disk to do my partition work .

---

### Post by VoidBoy on 2007-05-21
So, What exactly do you want to do with your partitions?........delet them? expand them? or what?
If you wan to expand them and your Hard Drive memory is not enough, an error might appear
Be more specific. ;)

---


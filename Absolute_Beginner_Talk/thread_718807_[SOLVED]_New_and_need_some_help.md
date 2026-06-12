---
title: "[SOLVED] New and need some help"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by einherjar_LC on 2008-03-08
Hello all and thank you in advance before you can give a true Linux greenhorn some assitance.

I have a computer I have partitioned for WinXP and Ubuntu 7.10.  I used partitioin magic 8.0 to arrange the partitons and I have bootmagic 8.0 installed as well.

The HDD is 160GB with 50GB for the Ubuntu ext3 and linux swap partiton, and the rest for WinXP.  Win XP is first on the partition with Ubuntu, then the swap file.

I can get Ubuntu to load up off the disk and update no problem.  I even restart the computer and I get the interface asking if I want Ubuntu, Ubuntu (recovery mode), Ubuntu memtest, or WinXP.  

If I choose Ubuntu each time the machine will boot flawlessly, but the first time I boot from that menu back into WinXP I am, from that point on unable to get back into Ubuntu.  

If I set the partition with Ubuntu to active, the start up screen hangs at verifying DMI pool data.

Any help is greatly appreciated.   

From what I have seen and used of Ubuntu, I am very pleased with it, but this is a real show stopper for me.  I have never had any problem getting multiple versions of Windoze to run on one box so this is frustrating me quite a bit.

Thanks!

---

### Post by handydan918 on 2008-03-08
The boot manager that comes with Ubuntu (GRUB) is quite competent at both detecting and loading Windows, as well as any other operating systems you may have. I would recommend removing your third party bootloader, and use GRUB. That way, if you do have a problem, there will be many people who can help you trouble shoot it. 
I have also had issues with third party partitioners...I have never needed anything other than the tools that come native to linux.

---

### Post by maniac_X on 2008-03-08
BootMagic is a boot manager if memory serves me correct. It's been a lng time since I used P.Magic and it's various tools. Could be that B.M. is causing the problem. Grub is basically the only boot manager you would need for a duelboot system. You said XP was first on the drive...so basically you have it as

[--------------XP 109GB(approximately)------------][----Ubuntu 50GB----][-swap1-]

I would start by dumping BootMagic and see what happens. Not sure if that might require some reinstalling of Windows or not but the above partition layout shouldn't cause any issues. It's a -almost typical- layout(swap might have been in the middle if Ubuntu was left to do the installing).

If I were doing the drive from scratch, I would just format 100GB NTFS and install XP and then just let Ubuntu utilize the remaining unpartitioned area. It usually does a good job of it. Just make sure if you do that to double check your selection.

edit: I second what handydan918 said since he was quicker than me, LOL! :)

---

### Post by einherjar_LC on 2008-03-08
Thanks for the replies.

I had a hunch as well it may be a conflict between partition/boot magic and GRUB.

I guess I am just so used to having to buy 3rd party utilities to get Windoze to do anything other than be a GUI for the internet.  

I'm not used to an OS being so self contained.

I am going to get rid of the 3rd party partitioner, merge the partitions back to one WinXP NTFS partition and have Ubuntu partition things out for itself and see how that works.

Will report back.

Thanks again.

---

### Post by einherjar_LC on 2008-03-08
Ok, it seems it was in fact a conflict between my 3rd party partitioner, Partition Magic and GRUB.

I did as I said in the above post letting Ubuntu configure everything and it works perfectly.

Thanks for all the help!

I think I'm gonna like it here  :)

---

### Post by steveneddy on 2008-03-08
> **einherjar_LC said:**
> Ok, it seems it was in fact a conflict between my 3rd party partitioner, Partition Magic and GRUB.

I did as I said in the above post letting Ubuntu configure everything and it works perfectly.

Thanks for all the help!

I think I'm gonna like it here  :)

Glad it worked for you. Could you mark this as solved?

Have fun and remember, we are all here to help you, so just ask.

Here is [a helpful link]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy").

---


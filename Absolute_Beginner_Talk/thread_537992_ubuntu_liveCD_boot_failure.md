---
title: "ubuntu liveCD boot failure"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by ouq77 on 2007-08-29
Hi. I'm relatively new to Linux, even though I have installed and worked with RedHat before.  My problem is that every time I try to boot up with the ubuntu liveCD, it only loads up to a certain point (loading hardware managers or loading PCMCIA managers...), then crashes.

I have created a seperate partition on my NTFS Windows XP hard drive and formatted it FAT32 using Partition Magic. I've also tried creating a Linux partition with Swap using Partition Magic, but no luck.

Any ideas? Thanx

---

### Post by henriette_holm on 2007-08-29
Have you tried checking the md5sum of the cd to see if it is corrupt in some way?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

/Henriette

---

### Post by ouq77 on 2007-08-30
hi henriette, thanks for yr reply. i will do that. however, i have two original linux ubuntu cd's.  one is version 6.06, the other is version 7.04. both runs into exactly the same problem. :confused:

---

### Post by be4truth on 2007-08-30
For the live CD you need minimum 512MB RAM. Do you have that?

---

### Post by DEagleson on 2007-08-30
If you got any problems with the LiveCD version, try using the Alternate version instead.

---

### Post by SunnyRabbiera on 2007-08-30
I have had a similar issue, but I personally wound up on another distro... solutions will vary ;)

---

### Post by ouq77 on 2007-08-31
Thanks to everyones replies so far. Yes, I have 1Gig RAM. Have tried 2 different liveCD's from two sources. Both has the same problem. It loads up to the point where it says "loading harware drivers" and then crash. 

I'm beginning to think that one of my hardware devices might be causing the problem... I've already unplugged all external usb devices. 

My computer however has a built-in storage card reader. Could that cause problems?  

How do I get hold of an alternative installation (not liveCD)? 

Can I burn and ISO image from the liveCD?

:(

---

### Post by dstew on 2007-08-31
You can get the Alternate Install image from the same download page where you get the regular (desktop) image. Just check the box below the green "Start Download" button. You cannot make an Alternate Install image from the LiveCD disk or image.

You can try boot options with the LiveCD. I think the first screen has an option for this, although I don't have a LiveCD in front of me, so I can't tell you exactly what to do. Sometimes, a graphics card gives the LiveCD problems, and you can use the option **vesa=force**. Other times, it might be the interrupt controller, and you can use the **noapic** option. I think you can get a list of options from the LiveCD intial screen.

However, the Alternate Install CD should always work.

---


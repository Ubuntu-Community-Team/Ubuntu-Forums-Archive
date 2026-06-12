---
title: "Anti-linux Motherboard???"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Asharale on 2007-11-03
I am trying to do an install on an Asus A7N8X-E Deluxe. I googled this model with linux and found descriptions like 'the worst motherboard for linux ever.' and 'a bane for linux users' 

I'm a newbie. Am I wasting my time trying to marry linux with this MS biased motherboard?

---

### Post by kellemes on 2007-11-03
Can you explain what's not working with the install of tux?

---

### Post by rickycodie on 2007-11-03
yeah now i'm intrested

---

### Post by Dr Small on 2007-11-03
How could a motherboard be "anti-linux" ?
I thought it just took whatever it was fed...

---

### Post by Toadmund on 2007-11-03
Why did I know this was going to be an Asus board?

My brother gave up on Ubuntu Linux because he got no sound, that's after fighting to figure out how to get connected, which he did eventually.

I'll stay away from Asus, unless...

---

### Post by Dr Small on 2007-11-03
> **Toadmund said:**
> Why did I know this was going to be an Asus board?

My brother gave up on Ubuntu Linux because he got no sound, that's after fighting to figure out how to get connected, which he did eventually.

I'll stay away from Asus, unless...
Please do not finish your sentance :p

---

### Post by Perfect Storm on 2007-11-03
I have ordered a new PC with an ASUS mother board and it's supported [http://www.phoronix.com/scan.php?page=article&item=506&num=1](http://www.phoronix.com/scan.php?page=article&item=506&num=1)

---

### Post by Jolly-Swagman on 2007-11-03
Some interesting reading on subject can be found here also

[http://www.yolinux.com/TUTORIALS/LinuxTutorialHardware.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialHardware.html)

---

### Post by Pumalite on 2007-11-03
I have an Asus motherboard and it's supported too. (mine is old though: P4P800 SE)

---

### Post by Asharale on 2007-11-03
Maybe its not anti linux, I can't get it to load. grub errors 17, 22, and now 18. I'm just worried that once I've figured out how to make it boot, I,'m going to run the gauntlet to get everything else to work. Nothing has been simple so far. I've learned a lot about how everything works. Maybe I should just get another Motherboard that won't confuse the grub. (I have to run raid. I can't get Grub and raid to get along)

---

### Post by Pumalite on 2007-11-03
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by phredduk on 2007-11-03
I've been running an A7N8X deluxe for almost four years on ubuntu with no problems whatsoever, so definitely not an anti-linux board!

---

### Post by Asharale on 2007-11-03
> **phredduk said:**
> I've been running an A7N8X deluxe for almost four years on ubuntu with no problems whatsoever, so definitely not an anti-linux board!

After you installed did you have to do anything different to get everything working or did the live disk have everything you needed?

thanks,
Rod

---

### Post by k33bz on 2007-11-03
Didnt realize that ASUS wasnt good for Linux. My desktop has a ASUS Gaming motherboard, which works 100% fine, (other than I burned up my CPU, cheap celerons grrr).  I had no problems at all, Linux worked right out the box, no tweaking or configuring needed.

I had more problems with my ACER laptop than with that motherboard.

---

### Post by Toadmund on 2007-11-03
I think that maybe my brothers asus board may have been too new.
By now its about 4+- months?
Perhaps he should try again to install Ubuntu?

I Can't remember what particular M2V-***  MOBO it is.

---

### Post by frank002 on 2007-11-03
I have the same board you have and dual-boot to XP Pro and Ubuntu Gutsy. Have not had any problems. I have been using Asus MoBos on the last 3 computers I have built and they have performed very well.

---

### Post by mirak63 on 2007-12-26
I exeprience lock ups and freeze with this motherboard. They are all recoverable, but that's anoying to have a movie freezing 10 seconds ...

---

### Post by Keith_Beef on 2007-12-26
This sounds like an old, old board... I had a similar one back in 2004. Back then, I had Mandrake 9 then 10; it's  still going strong with Ubuntu on it.

Some people have reported that it needs noapic nolapic options to get good uptimes, but I didn't need to do that.

B.

---

### Post by Keith_Beef on 2007-12-28
> **Asharale said:**
> Maybe its not anti linux, I can't get it to load. grub errors 17, 22, and now 18. I'm just worried that once I've figured out how to make it boot, I,'m going to run the gauntlet to get everything else to work. Nothing has been simple so far. I've learned a lot about how everything works. Maybe I should just get another Motherboard that won't confuse the grub. (I have to run raid. I can't get Grub and raid to get along)

Grub errors: [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

I never tried SATA RAID on my A7N8X-E. I think that at the time, SATA drives were too expensive for me, and I think I remember reading that the SiL 3112A controller was not fully supported by Linux back then.

A quick bit of [Googling ]("http://www.google.com/search?q=SiL+3112A+controller+linux&ie=utf-8&oe=utf-8")gave me a few interesting stories.

Looking at the manual for the A7N8X-E, this board (or rather, the controller) only does RAID 0 (striping) or RAID 1 (mirroring). You mention 
> **Asharale said:**
> I have to run raid

Maybe you could get a RAID PCI card that is known to work, or just bite the bullet and get an external RAID NAS enclosure. Boot from a small internal drive (IDE or SATA, whatever) and use the NAS for storage of your critical data.
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000092&Description=RAID&name=External+Enclosures](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000092&Description=RAID&name=External+Enclosures)

B.

---

### Post by Sef on 2007-12-28
> I exeprience lock ups and freeze with this motherboard.

Could be a bad motherboard.   I had the the same problem.  Did a mem86 test and found that my memory module was bad.   (It would stop at test 8.)   I would recommend you do that and see if either your memory or that part of our motherboard is bad.

---


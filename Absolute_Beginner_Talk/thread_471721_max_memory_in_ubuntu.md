---
title: "max memory in ubuntu?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by nickburns on 2007-06-12
I upgraded my memory in my Dell to 4 gigs, the motherboard / bios sees that I have 4 gigs, but when I run 'top' I only have 3 gigs.  Is there a max memory for linux?  or do I need to configure something?

---

### Post by insane_alien on 2007-06-12
some adresses arereserved for devices and operations. this wasn't a problem till we started maxxing out 32-bit address spaces. if you have a 64-bit processor then you should probably upgrade.

---

### Post by rscott5 on 2007-06-12
So does a 32-bit proc running in Ubuntu 7.04 support more than 3GBs of memory? You're answer wasn't clear.

---

### Post by MrMatt2532 on 2007-06-12
> **rscott5 said:**
> So does a 32-bit proc running in Ubuntu 7.04 support more than 3GBs of memory? You're answer wasn't clear.

No it doesn't. At least not normally. But a 64-bit version will support your 4 GB if you have a 64-bit processor.

---

### Post by nanotube on 2007-06-12
according to [http://www.extremetech.com/article2/0,1697,2114123,00.asp](http://www.extremetech.com/article2/0,1697,2114123,00.asp)
the max addressable memory on 32bit is 4g, including swap. so if you have 1g swap... there goes that 1gb.
some ram out of that 4g also goes to addressing various pci devices, etc...

might also want to look at [https://answers.launchpad.net/ubuntu/+question/6732](https://answers.launchpad.net/ubuntu/+question/6732)
and the "bigiron" kernel...

---

### Post by Lord Illidan on 2007-06-12
Would you need swap with 4 gigs of RAM? I'd just remove the swap if I were you. If 4 gigs is the limit, 3 gigs of RAM with 1 gig of swap is still slower than 4 gigs of RAM with no swap.

---

### Post by starcraft.man on 2007-06-12
> **nanotube said:**
> according to [http://www.extremetech.com/article2/0,1697,2114123,00.asp](http://www.extremetech.com/article2/0,1697,2114123,00.asp)
the max addressable memory on 32bit is 4g, including swap. so if you have 1g swap... there goes that 1gb.
some ram out of that 4g also goes to addressing various pci devices, etc...

Ah, I see. So the Swap size and physical ram are added together. So if you have 4 GB of physical ram on your machine, only way to have Ubuntu use all that is to make a negligible/no swap file. Question though, will having no swap cause any detriment to system if you have that much physical ram? Or I s

Edit: nvm guess Illidan answered my question >.>

---

### Post by rscott5 on 2007-06-12
> **MrMatt2532 said:**
> No it doesn't. At least not normally. But a 64-bit version will support your 4 GB if you have a 64-bit processor.

Damn that puts a damper on my new PC plans ;-) . Eh well, guess I'll just stick with 3GBs and a 1GB swap.

---

### Post by drummingpariah on 2007-06-12
Well, just because RAM can't hold data when it isn't being powered.  If you want to hibernate, you'll need swap.  Other than that, I don't see any reason.

---

### Post by nickburns on 2007-06-12
Thanks for all the help.  This is my work PC.   I guess I will have to request a 64 bit computer from my boss.  Is the 64bit ubuntu up to the same standards as 32, I have had nothing but a good time with 32 and don't want trouble.

Can I run vmware on 64 bit?

---

### Post by starcraft.man on 2007-06-12
> **nickburns said:**
> Thanks for all the help.  This is my work PC.   I guess I will have to request a 64 bit computer from my boss.  Is the 64bit ubuntu up to the same standards as 32, I have had nothing but a good time with 32 and don't want trouble.

Can I run vmware on 64 bit?

Well like Illidan pointed out you can just shrink your swap file to an insignificant size like 128/256 if you want to keep the option for hibernate (I think thats all it needs, I don't hibernate often so it may be more less). Or just wipe it out all together. Are you really going to use all 4 GBs of ram?

I recommend against 64 bit... I just don't think its worth the hassle I've seen lots of people go through, it does depend on what specific set of apps you want. The world's still 32 bit, I'll have to check but I think VMware has a 64 bit host version.

Edit: Yes, there is a functional version of VMware for linux.

---

### Post by DBStevens on 2007-06-12
You are seeing a normal 3gb/1gb split for the 4gb memory model of a 32 bit processor.

There are many possible memory mappings availible if you configure a kernel for it.

I just looked at the configuration of the current kernel version on ubuntu and it is one that can use up to 4GB with the first 3GB availible for a task and the remainder used exclusively by the kernel.

[This is how it all goes together]("http://www.ibm.com/developerworks/linux/library/l-memmod/")

32 bit Intel processors with PAE can address up to 64GB of memory if you can get it installed on your motherboard.   This adds another level in the page tables.

---

### Post by Inxsible on 2007-06-12
Lots of software have issues running on a 64-bit OS architecture. They can run, but you would have to tweak them a bit. I, for one, would recommend against it.
 
I have a 64-bit processor, but I use the 32-bit Ubuntu.

---

### Post by Skilly on 2007-06-13
I have a similar query. I have just upgraded my latop (running Dapper) from 1GB to 2GB RAM and was wondering whether I needed to adjust SWAP space. I found the following comment 

***"The second limitation comes from the Linux 2.6 kernel used by Ubuntu's Dapper Drake (as well as other Linux variants). The kernel can only access 1 GB of RAM."***

on this webpage --> [http://www.extremetech.com/article2/0,1697,2114123,00.asp]("http://www.extremetech.com/article2/0,1697,2114123,00.asp")

Does anyone know if this is accurate?

---

### Post by drummer on 2007-06-13
In regards to installing 64bit Ubuntu (whoever it was that asked), I've just installed 64bit Feisty this week (been using 32bit on my 64bit cpu until now) and have had no problems so far. 64bit Ubuntu has definitely come a long way and the only thing I had to do differently was install a 32bit flash plugin for Firefox with an app called nspluginwrapper, which was easy anyway.

So unless you use some unique applications that aren't in the repos or are proprietry and with no 64bit version, it seems like pretty smooth sailing from here.

I also have VirtualBox (like VMWare) installed with a 32bit WinXP guest OS.

64bit computing is MUCH less of a headache than it was a year ago.

---

### Post by hyper_ch on 2007-06-13
Hmmm, as far as I read and understand here you just have to use a 64bit processor to use more than 3gb ram... right? You aren't required to run a 64bit OS?

---

### Post by nickburns on 2007-06-13
good point, Can i get 64 bit hardware and have a 32 bit software and run more memory?

---

### Post by rscott5 on 2007-06-13
So say I get a 32-bit system with Ubuntu Feisty and install 4GB of RAM, and just have a 128MB swap partition...will I be able to access 4GB - 128MB of my physical RAM?

---

### Post by Rui Pais on 2007-06-20
> **Inxsible said:**
> Lots of software have issues running on a 64-bit OS architecture. They can run, but you would have to tweak them a bit. I, for one, would recommend against it.

Maybe in the past. Right now, thats not true. 

And 32b apps runs on a 64b environment, so in case of worst you can always install the 32versions of the problematic one...

---


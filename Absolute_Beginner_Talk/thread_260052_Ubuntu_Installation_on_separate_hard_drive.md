---
title: "Ubuntu Installation on separate hard drive"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Ghese on 2006-09-18
Hi 

I have a company laptop (Thinkpad T41) and would like to install Ubuntu (Dapper Drake) without messing up my Windows data.  Instead of installing on my current hard drive is it possible to install Ubuntu on a separate hard drive?  Is this compllicated? Is there any documentation on the same?  Can someone send me a link?

---

### Post by timmeeej on 2006-09-18
Yes it's possible and it's not really complicated. You have two options:
1. Install Ubuntu on your second harddisk and put your bootloader on the MBR of your Windows harddisk. When you boot your computer you will get a Grub bootloader screen asking your if you want to boot Ubuntu or Windows.
2. Install Ubuntu on your second harddisk and put your bootloader on second harddisks MBR. You can now switch between Ubuntu and Windows using your Bios boot settings.

[SIZE="1"]3. Format your windows partition and throw away your Windows cd :-\" [/SIZE]

---

### Post by Ghese on 2006-09-18
Thanks for the quick reply but I don't understand what 'bootloader' and 'MBR' mean. I'm really not a techie person but I'm willing to learn.  How do I install Ubuntu on the second hard drive?  I have a live CD.  When I choose 'install' do I get the option on which hard drive I can install?

---

### Post by Linux Lover on 2006-09-18
you please tell me nos. of hard discs you have, also the size and no. partitions partitions you have in all your hard discs.

---

### Post by Ghese on 2006-09-18
> **Linux Lover said:**
> you please tell me nos. of hard discs you have, also the size and no. partitions partitions you have in all your hard discs.
I have not bought an extra hard drive yet.  I have a hard drive on my laptop.  I'm debating if i should buy an extra hard drive or a laptop itself.  How do I find out the no of partitions on my local hard drive?

---

### Post by dckirba on 2006-09-18
I just installed Ubuntu at home on a second hard drive. I used the alternate install cd.

If both your hard drives are the same size, please make sure you know which one is the empty one you're going to use for Ubuntu.

I did this by using a live cd and then running **fdisk -l** in a terminal just to make sure I knew which one was the new one.

after you boot with the alternate cd, choose your new hard drive, hdb in my case, and format the entire disk and install from there. The rest of the install is pretty painless, but there's a great manual here: 
for the live cd: [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
for the alternate cd: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

If you're not too sure about something, take some time to read and ask around and don't install unless you're ready to do it. The more you read, the less confused you get when an option or a question pops up. 

I hope this helps, have fun,
David K

---

### Post by Linux Lover on 2006-09-18
> **Ghese said:**
> I have not bought an extra hard drive yet.  I have a hard drive on my laptop.  I'm debating if i should buy an extra hard drive or a laptop itself.  How do I find out the no of partitions on my local hard drive?

Thank you for your answer.

My friend, first I convey my wish to you for your choise to install ubuntu. In my opinion, it is not only the easiest linux but uses the recent kernels and you can get it absolutely free too even with its updates. This linux distribution also uses all of the softwares in its recent and updated versions.
To install such a nice operating system you need some free space in your hard disc. As you have installed your windows in a partition named c:, similarly you need another partition to install ubuntu. In windows, if you double click on MyComputer, it will show you some c:, d:, e: etc. as your drives. Lets check which one are your hard drives and which one are your CD drives. Then send the nos. and size of the hard drives.

---

### Post by Ghese on 2006-09-18
> **Linux Lover said:**
> Thank you for your answer.

My friend, first I convey my wish to you for your choise to install ubuntu. In my opinion, it is not only the easiest linux but uses the recent kernels and you can get it absolutely free too even with its updates. This linux distribution also uses all of the softwares in its recent and updated versions.
To install such a nice operating system you need some free space in your hard disc. As you have installed your windows in a partition named c:, similarly you need another partition to install ubuntu. In windows, if you double click on MyComputer, it will show you some c:, d:, e: etc. as your drives. Lets check which one are your hard drives and which one are your CD drives. Then send the nos. and size of the hard drives.
My local disk 'C' has about 40 GB of which about 9 GB is free.  The other one is the CD drive 'D'.  Does that help?

---

### Post by Ghese on 2006-09-18
> **dckirba said:**
> I just installed Ubuntu at home on a second hard drive. I used the alternate install cd.

If both your hard drives are the same size, please make sure you know which one is the empty one you're going to use for Ubuntu.

I did this by using a live cd and then running **fdisk -l** in a terminal just to make sure I knew which one was the new one.

after you boot with the alternate cd, choose your new hard drive, hdb in my case, and format the entire disk and install from there. The rest of the install is pretty painless, but there's a great manual here: 
for the live cd: [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
for the alternate cd: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

If you're not too sure about something, take some time to read and ask around and don't install unless you're ready to do it. The more you read, the less confused you get when an option or a question pops up. 

I hope this helps, have fun,
David K
David K, thanks for that reply.

---

### Post by Linux Lover on 2006-09-18
> **Ghese said:**
> My local disk 'C' has about 40 GB of which about 9 GB is free.  The other one is the CD drive 'D'.  Does that help?

So, you have a 40GB Hard drive and all the space used as a single partition. It is being marked as c: and there is another CD drive which is being marked as d:

Sorry friend, to install ubuntu as your second operating system, you need repartition your hard disc.

Take an example of how much partition you need to install these two operating systems.

Partition 1 (/dev/hda1 or C: ) 20 GB : To be used by windows
Partition 2 (/dev/hda2 or D: ) 5 GB : To be used to save your windows files
Partition 3 (/dev/hda3) Linux SWAP : 2 * size of your RAM
Partition 4 (/dev/hda4) Linux root partition : Use rest of the space for ubuntu linux.

This is an example and you may have another idea too. Anyway, it will need formating of all the partitions which means loss of data. So, you can proceed only if you have enough back up only. Think twice before proceed.
Once you repartition, you cannot get back your previous data.

---

### Post by bulldog on 2006-09-18
9 GB is not enough to comfortably install Ubuntu on.

You should run out of space in Ubuntu an windows as well.

You can see if you can free up more space or a second hdd.

The next question is how do you put a second hdd in your laptop??

It will not run from an extern hdd!!!

---

### Post by Ghese on 2006-09-18
> **bulldog said:**
> 9 GB is not enough to comfortably install Ubuntu on.

You should run out of space in Ubuntu an windows as well.

You can see if you can free up more space or a second hdd.

The next question is how do you put a second hdd in your laptop??

It will not run from an extern hdd!!!
Thanks a lot for the info.  You hit the nail on the head.  I just found out from the store that an external HDD was not the solution.  Does that mean I have to get an HDD that can be integrated internally into my laptop?  I found this text as part of my laptop config "You can install either an Ultrabay Slim device or an Ultrabay Enhanced device in the Ultrabay Enhanced. You cannot install an Ultrabay 2000 device or an Ultrabay Plus device."  I guess that is only from IBM/lenovo, right?

---

### Post by bulldog on 2006-09-18
Well that's a question and I know no answer :biggrin: 

Go to the manufacturer site or the shop where you bought it,they should know.

You can put in a larger hdd that's for sure but which type..........I don't know.

Concider you need certainly 20 -30 GB for Ubuntu and the same amount for Windows at least.

Look for a hdd of 80 GB and it should be enough for the time being.
Be carefull to buy one with 7200 rpm and not 5400 rpm cause they are really slow.

---

### Post by Ghese on 2006-09-18
You are a STAR.  I also wanted to know a good hardware config.

---

### Post by bulldog on 2006-09-18
> **Ghese said:**
> You are a STAR.  I also wanted to know a good hardware config.

Meaning?

You want the config of a laptop.

---

### Post by Ghese on 2006-09-18
> **bulldog said:**
> Well that's a question and I know no answer :biggrin: 

Go to the manufacturer site or the shop where you bought it,they should know.

You can put in a larger hdd that's for sure but which type..........I don't know.

Concider you need certainly 20 -30 GB for Ubuntu and the same amount for Windows at least.

Look for a hdd of 80 GB and it should be enough for the time being.
Be carefull to buy one with 7200 rpm and not 5400 rpm cause they are really slow.
Bulldog, I'm using my company laptop and I may have to buy a personal laptop because I would have to justify getting a bigger HDD.  Can you also point me to a good hardware config for ubuntu?

---

### Post by bulldog on 2006-09-18
For Ubuntu you don't need a rocket computer but there are some things to concider.

Any modern processor of AMD or Intel would do.

If you have the choice for a graphics card try to get a nVidia.

Hard disk 7200 rpm would be nice :lol: 

I'm not known with WiFi and stuff,sometimes it works and other times.......well,I don't use it.:cool: 

Maybe you can get help from someone who have experience with this part.
 

Don't think there are other things to concider,I have a laptop too and all works right out of the box exept that WiFi thing. [didn't looked into it]

---

### Post by Ghese on 2006-09-18
Once again, thanks a lot to everyone for all the information.

---


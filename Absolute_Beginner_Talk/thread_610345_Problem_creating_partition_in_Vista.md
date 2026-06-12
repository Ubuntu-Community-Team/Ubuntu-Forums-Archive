---
title: "Problem creating partition in Vista"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by velaxun on 2007-11-11
I bought a new computer with Vista a couple months ago, but now I'm starting to get bored with it and was thinking of trying out Ubuntu 7.10 I have the CD and everything but I don't want to install it over my Vista installation because I would like to go back and forth between the two.

Now, here's my problem. I've been trying to use the Disk Management tool that came with Vista. I have a 320GB Seagate HDD but whenever I want to shrink the volume, it'll only give me a max of about 7gb. I need more than that for tooling around in Linux. So I tried to defrag and see if I could get some more space. This time it said it would give me less. So I'm like "screw it" I'll try it and expand it in Linux if I have to. Well lo and behold, the shrink fails for no reason at all. It tells me to check the system event log, but I don't know where to look or how to get there.

Attempt number 2 was to use the Diskpart utility that came with Vista. I follow the instructions that I found and tried to create a partition with a max of 20GB and failing that a min of 10. Diskpart says that "The specified shrink size is too large". So I try something else, I tell it to shrink what it can. It turns around and says "DiskPart has encountered an error: Access is denied. See the system event log for more information"...wtf... there's the event log again.

So I come here seeking aid, how can I go about creating a partition big enough to install Ubuntu 7.10 on a computer that has been running Vista. Google failed me, so I'm hoping someone here can help.

PS I'm a total noob when it comes to Linux so sorry if there's an obvious answer that I don't know:(

EDIT: I saw elsewhere that you can use GParted to modify the partitions, but I can't seem to get the Live CD to boot. I'll get the first part with the options to start the install, run Memtest etc. So I click on Start or Install Ubuntu and and wait for it to boot. After a while my CD light starts flashing and the Hard drive starts doing stuff too, then an orange screen shows up and a little music plays. Then everything stops. I've been waiting for 20 minutes and nothing has happened, is this normal?

---

### Post by DutyDuty on 2007-11-11
To create a partition, just run the live CD and follow the instructions.

---

### Post by velaxun on 2007-11-11
I'm an idiot, I moved my mouse and the screen wasn't black anymore >.<

So if I run the install from the live CD it would create a partition that I could use to dual boot Ubuntu right? Because I want to install it alongside my Vista install

---

### Post by Thor (Hammer of God) on 2007-11-11
> **velaxun said:**
> I'm an idiot, I moved my mouse and the screen wasn't black anymore >.<

So if I run the install from the live CD it would create a partition that I could use to dual boot Ubuntu right? Because I want to install it alongside my Vista install
Well, be carefull... The defaults will certainly rebuild your partitions, but you'll loose what you have now... So don't just install from the Live CD unless that is what you want.  Shrink volume is the best way to do, but the "shrink size available" can be limited by your page file, a hibernation file, etc.  You should also note that your MBR will most probably be replaced by the Ubuntu install; so if you don't have a boot disk manager (like Acronis) then you'll have to boot off your Vista CD in console mode and run BOOTFIX to get it back.  This is true even if you try to install to a USB - your HD0 MBR will get overwritten (did it to me several times) so I just disabled all my SATA2 controllers and booted to a little 80 USB drive.  It's a really nice way to go, so you might also look at that as an option.

---

### Post by velaxun on 2007-11-11
So then I should try to make another partition in Vista if I plan on dual booting right? Otherwise, if I try using the LiveCD installer it would erase everything from the vista partition and I would lose everything correct?

---

### Post by Thor (Hammer of God) on 2007-11-11
> **velaxun said:**
> So then I should try to make another partition in Vista if I plan on dual booting right? Otherwise, if I try using the LiveCD installer it would erase everything from the vista partition and I would lose everything correct?
Yes - that's exactly what will happen.  Just to be safe, you should probably get a backup of your files if you don't already have one.  I've not had problems with Vista's partition managment tools, but friends have.  When you are messing around with your partitions, it's good to have a backup first. 

But yes, it's best to create your partition first, or at least shrink your Vista partition and leave the other space unallocated and let Ubuntu's Partition Manager create it for you in "manual" mode.  But, like I said before, if you have the option of installing to a USB drive (you can get them pretty cheap) I think that's a "cleaner" way to do it-- you don't run the risk of losing what you have, you don't have to worry about boot managers, and you can use the install defaults when you have to reinstall Ubunutu (which you'll probably have to do if you're just getting into it -- I know I did).  Short of that, shrink your volume in Vista, leave the space unallocated, then install Ubuntu there.

---

### Post by velaxun on 2007-11-11
ok, I'll try doing that. I just need to get the partition manager working. I've already backed up my files so I won't install to a USB Drive. Do you know anyway to make the partition that vista creates bigger? Mine only wants to free up 7gbs of space

---

### Post by Thor (Hammer of God) on 2007-11-11
Interestingly enough, this guy also had only 7 gig free:
[http://articles.techrepublic.com.com/5100-10877_11-6170510.html](http://articles.techrepublic.com.com/5100-10877_11-6170510.html)

The article discusses why you are limited in available shrink space.  Though it didn't do the author any good, you could try disabling the page file, shadow copies, hibernation files, etc, reboot and see if you have more space available.  
hth
t

---

### Post by velaxun on 2007-11-11
I'm still getting an error everytime I try to shrink the volume, here's a picture of the error if you or anybody else knows what to do with it:confused:

[[IMG]http://img162.imageshack.us/img162/1711/wtfii1.th.jpg[/IMG]](http://img162.imageshack.us/my.php?image=wtfii1.jpg)

---

### Post by Thor (Hammer of God) on 2007-11-12
What does your system log say?  Any more details than that?

---

### Post by acegeezer on 2007-11-12
Use Partition Magic, does a free trial (once is enough for you right) to reduce your Vista partition and like, has already been said let Ubuntu Live CD partition your linux OS and make sure to do it manually, you don't want to format your vista OS, now do you?

---

### Post by vistabuntu on 2007-11-12
Hi all, Im new to ubuntu.............. currently Im using Vista  ultimate and I have several hard drives installed. 

My question is    ,, Can I install Ubunta on a seperate drive and if so will it be dual boot ?

If yes to above what will I need to  do it and do I need to install from boot?

The reason I ask is cause I tried from boot and all it did was  stay stuck on screen for a long time and on the bottom it said 

kernel mapping from 120000000000000000@8000-e  something like that . 

Oh ,, can someone point me in right direction to a dual boot guide for ubuntu ?  

Amd X2 dual core 5500 64 bit
Vista Ult. 32 bit
4gigs of ram 
4 Hds  (sata)
Geforce 7900
and Hopefully Ubuntu 7.10

Thanks

---

### Post by Thor (Hammer of God) on 2007-11-13
That might be a good idea... The last time I went to shrink a volume, both Vista and Acronis reported the same "shrink space available" but I just checked and they are different (Acronis show 14 gig more available, which is still strange since I've got a terabyte).  I'll do some research and see exactly what this is actually based on.

t

---

### Post by Thor (Hammer of God) on 2007-11-13
> **vistabuntu said:**
> Hi all, Im new to ubuntu.............. currently Im using Vista  ultimate and I have several hard drives installed. 

My question is    ,, Can I install Ubunta on a seperate drive and if so will it be dual boot ?



I'm new too, but I'll tell you my experience.  I also have quad 500 gig SATA2's, but they 2 are in a stripe with the other 2 miroring that stripe hardware raid.  Unfortunately, HP does not have a Linux driver for my raid card, so Ubuntu would only see the actual drives, and not the logical drive.

Because of this, I thought it best to just install on an USB drive - initially, when I installed ont he USB drive, ubuntu still altered the MBR of HD0 - neither Vista x64 nor ubuntu would boot.  That, however, was quickly fixed with BOOTFIX from the Visat install cd.  In order to properly install, I had to diable both sata controllers, thus letting ubuntu only see the USB drive.  That actually works out just fine now- after re-enabling sata, if the usb is plugged in, ubuntu boots off the usb, otherwise, Vista boots off the hard drives.  

Regarding the actual multi-boot capabilities, my thought is that you'll need some sort of boot manager (or you'll have to properly edit the boot info for Vista) to do what you want.  If I set my HD to boot first, I can use Acronis Boot Manager to boot Vista, my XP game partition, or the Ubuntu USB drive- but that's a 3rd party utility (which I recommend because they officially support Vista x64, and their partition utilities are more robust than the default Vista functions).

hth
t

---

### Post by vistabuntu on 2007-11-13
Hmmm, My board has only 1  Ide device and six internal sata and my Raid is disabled. 
I have four Hds on individual Sata ports. I cleaned out 1 500 gig drive four Ubuntu. So ,, what your saying is ,, if I install it on that 500 gig drive from "a boot from cd" the Master Boot  Record will rewrite .

Now the second things is ..... is it a normal thing when it just stays on a black screen  with .......................


kernel mapping from 120000000000000000@8000-e on the bottom of the screen

---

### Post by vistabuntu on 2007-11-14
Follow up: I read thru the forum and found a few things out . Turns out I can just install Ubuntu on any of my drives as long as Vista is installed first.  Just in case I obtained a copy of Acronis. 

I had no luck with 7.10(64 bit) as it just hangs during boot up so I tried 6.06(64 bit) and it loads and goes thru the motions but it also hangs with a screen that says  ubuntu and a progress bar. 

Dont know if thats the norm but after  30 mins and doing some chores at home the screen doesnt change so I reboot and try again . Ive searched the forums to find if anyone else has  the same problem but found nothing . 

Anyways Ill keep messing around with some settings .

---


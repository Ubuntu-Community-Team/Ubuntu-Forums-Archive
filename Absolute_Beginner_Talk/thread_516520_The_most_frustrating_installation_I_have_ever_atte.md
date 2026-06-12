---
title: "The most frustrating installation I have ever attempted ..."
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by boomcat on 2007-08-03
... by several orders of magnitude.

I’m trying to install Ubuntu 7.04 on a seldom-used IBM Thinkpad laptop, a T20 (Pentium-3 at 700 mHz, 12-gig HD, 256-M RAM). This was running Win 2K Pro SP4, but I just wanted to do a “clean install” of Ubuntu over it. This would be my first Linux machine.

I downloaded the Ubuntu i86 Live-CD version onto my P4 desktop computer, ran the hash check on the download and burned it to a CD using InfraRecord.

I booted the T20 to the CD. It took a LONG time to display the first Ubuntu installation screen. I selected “Start or Install Ubuntu”. The CD drive and the HD drive went into continuous activity for ten minutes, but nothing happened. I powered down the T20 and did some reading. It said that I should burn at the slowest speed possible, so I tried burning at the slowest speed. That disk booted and gave the same results. Bedtime!

The next day I pored over websites and forums, looking for hints. I learned about ACPI. I learned about “splash=quiet”. I learned to replace “driver=savage” with “driver=vesa”. Using these techniques I was able to get to the first installation screen and I heard the music for the first time. I double-clicked on “Install” and the first screen (“Welcome”) appeared, but the “Forward” button was grayed-out. After an hour of continuous CD and HD activity it was still grayed-out. Bedtime!

The next day I stopped by the Barnes and Noble after work and got a book-CD combo “Ubuntu for Non-Geeks”. This book included a commercially-made installation of i86 Desktop, and this one not only booted, it took me to the first installation screen and played the music! But when it reached the “Welcome” screen it got stuck. After 30-minutes of continuous CD and HD activity the “Forward” button was still grayed-out. After a lot more Internet research I read that the “Live-CD” installation is very resource-intensive, particularly for older machines, so I downloaded the “Alternate” i86 version, ran the hash check and burned it to disk using InfraRecord. That disk wouldn’t boot. I burned another copy but that one failed to boot, too. Bedtime!

The next day I tried using Nero to burn the ISO image of i86-Alt, so I could verify the results. The first attempt wouldn’t verify after burning. Neither would the second attempt. But that was my last CD so I decided to try the second one anyway and it DID boot! And I got into the text-only installation all the way to “Loading base” before it crashed. I had used up all of my Memorex CDs by now, so I bought some “data-quality” Maxell CD-Rs to replace them. I used my P4 and Nero to burn a CD image of i86-Alt onto a Maxell CD-R at 1X speed. This version DID verify! But it would not boot. I did more research. Bedtime!

The next morning I got up at 5:00 AM and booted up my son’s desktop computer; it has a CD-RW drive. My own computer has a DVD-RW drive and my thought was that there might be an incompatibility between that and the CD-ROM drive on the T20. I had already tried two distributions, two brands of CD and two CD burn programs, so the drives were the only remaining possibility. I transferred the ISO file over my home network to my son’s computer. I installed Nero and InfraRecord. I burned a Maxell CD with InfraRecord. It wouldn’t even boot: “no operating system found”. Then I burned another Maxell CD with Nero, so I could verify it. It verified! But it wouldn’t boot, either: “no operating system found”. This worried me so I tried to boot the commercial CD that came with the book; it wouldn’t boot, either: “no operating system found”. I went into BIOS and “locked out” the HD as a boot device, just in case the computer was trying to boot to a badly-installed crashed installation on the HD. Computer won’t boot: “no operating system found”.

So I’m dead in the water.

I used to do programming in 8086 Assembler for floating-point math coprocessors. Remember when you had to buy a separate math coprocessor, and it cost over $200? That was difficult, but nothing like this Ubuntu experience!

---

### Post by apswartz on 2007-08-03
See if this helps any...
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20)

---

### Post by Peter76 on 2007-08-03
Sorry to hear you have so much troubles.... One thing I can think of is try booting the cd(s:-) in one of your other computers and see if they work there... It's weird the T20 doesn't even boot anymore. You also might try the alternate install cd; could be you're a bit low on memory... Good Luck

---

### Post by Inxsible on 2007-08-03
I think your system is a bit old for Ubuntu. But Xubuntu(which has Xfce as the WM instead of Gnome) would be a good bet.

Another light distros include Fluxbuntu, Damn Small Linux, Puppy Linux and a bunch of others.

Give those a try and see if they work for you.

---

### Post by dca on 2007-08-03
On a Thinkpad T20 I don't remember having any problems w/ the 6.06LTS Desktop Ed...  The only thing that caused a hang-up was the WiFi installed...

---

### Post by TheGreatGonzo on 2007-08-03
Boomcat

I started out with Linux on a Thinkpad R40e and had real trouble.

The two things that helped me were :

1./ Disable the USB boot option in the Bios (if it exists in your Bios).
2./ Format the whole drive.  The drive that came with thr R40e had a rescue partition on it in the first 4gig.  This caused me all kinds of problems.

I have also over time had problems with burning distros in windows but found a (free) windows solution in a program called burnCDCC.  Point it at a iso and a blank cd and it "just works".  Google for it but if you can't find it let me know and I will happily zip and mail it to you.

Sorry your having a baptism of fire!!

Good luck

gonzo

---

### Post by Inxsible on 2007-08-03
I have a ThinkPad T42, and it has an ATI card in it. I am not sure what the T20 has or rather what your specific machine has, but ATI cards are not known to be Linux friendly, maybe thats why you can't go beyond the welcome screen.

---

### Post by boomcat on 2007-08-03
Gonz,
I will definitely try burnCDCC. Thanks for the encouragement.
When you say "format the whole drive" do you mean boot from a Windows CD and re-partition and format in FAT32? Or what?

---

### Post by apswartz on 2007-08-03
> **boomcat said:**
> Gonz,
I will definitely try burnCDCC. Thanks for the encouragement.
When you say "format the whole drive" do you mean boot from a Windows CD and re-partition and format in FAT32? Or what?

No, he means let the install program completely reformat your entire hard drive, wiping out everything on it.

---

### Post by bluenova on 2007-08-03
After everything you have tried it sounds like the cd-rom drive on the T20 has had it's day.

---

### Post by boomcat on 2007-08-03
> **bluenova said:**
> After everything you have tried it sounds like the cd-rom drive on the T20 has had it's day.

Yeah, that's definitely high on my "suspects" list.

---

### Post by Inxsible on 2007-08-03
> **boomcat said:**
> Yeah, that's definitely high on my "suspects" list.

To verify the suspicion, you can go into the LiveCD. Instead of selecting Install, open a terminal and do a ```
sudo fdisk -l
``` -l is lowercase L. This will show you all your drives and partitions on them. If nothing is read, then you would have nailed your suspect. Incarcerate him(it) !!

---

### Post by Outrunner on 2007-08-03
[This]("http://www.bizrate.com/laptopcomputers/ibm-thinkpad-t20-700-mhz-pentium-lll-laptop--pid11488873/information.html")  page says

> CD Read Speed:  	 6 X

Well, Live CD or Alternate CD, it will be painfully slow to load.

---

### Post by boomcat on 2007-08-04
Well, I fixed it. I don't know how exactly. The T20 would boot to the CMOS splash screen but since the HD was only half-partitioned, the HD wouldn't boot and the CD wouldn't boot either. I took the dozen CDs that I had burned and, on another computer running Win 2K, I booted each of them to the Install window and selected "Check CD Integrity". I had to throw away seven of the twelve CDs that I had made. I also went to the Lenovo site and D/L'd two ISOs of bootable CDs, one for updating CDROM firmware and the other for updating HD firmware. 
I put the former into the drive and started up the T20 and the damned thing booted! I could hardly believe it! I updated the CD firmware, then rebooted with the other CD and updated the HD firmware, too. Then I put in one of my "known-good" install disks of Ubuntu 7.04 i86 Alternate, and booted to that and the whole install went like a dream. I'm writing this on the T20.
In retrospect it may have been a slightly tarnished connector at the HD or CD. Several times I powered down, removed both batteries and both drives and let the T20 sit for 15 minutes or so before reassembling and and making another attempt. Another lesson learned is to check your installation CD on another computer before attempting installation. I hate to think of how many times I must have attempted to boot to a bad CD, but I blamed it on the computer.

---

### Post by Peter76 on 2007-08-04
Good to hear you solved it and are up and running now

---

### Post by apswartz on 2007-08-04
Fantastic!

---


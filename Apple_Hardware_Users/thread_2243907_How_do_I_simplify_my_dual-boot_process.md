---
title: "How do I simplify my dual-boot process?"
date: 2014-09-11
forum: Apple Hardware Users
---

### Post by dcnicholls on 2014-09-11
I have just installed Ubuntu v 12.04 as a dual boot on my old MBP (5,3) running Snow Leopard.  It works, but the boot process is a bit complicated and I'd appreciate advice on how to make it simpler.  Here's how it goes at the moment:

Settings: I have the following disk partitions:

sda            465.8G            
&#9500;&#9472;sda1 vfat      200M /boot/efi  EFI
&#9500;&#9472;sda2 hfsplus 418.9G            Macintosh HD
&#9500;&#9472;sda3 ext4     37.4G /          
&#9492;&#9472;sda4 swap      9.3G [SWAP]     
sr0             1024M  

[Aside, and probably irrelevant: I had originally set aside a vacant 50Gb on the disk to set up Ubuntu on, but the about Ubuntu map seems to suggest that the Ubuntu install gobbled 50Gb from the existing OS X partition, leaving the vacant disk still empty. OTOH, Disk Utiliy on OS X says all is well, and Macintosh Hard Disk has ~450 GB, with Ubuntu occupying a further ~40Gb and Swap a further 10Gb.  So I don't know which one to believe.]

I have rEFIt installed on OS X (rEFInd seemed to be having problems with the grub menu, so I removed it and installed the older rEFIt,  but I'm not absolutely sure what was going on)

The boot proceeds as follows:

If I turn on the MBP in the standard way, I get the rEFIt menu options that include Ubuntu (two options) and Mac OS (and a few other small buttons for shutdown etc). The Mac option boots as expected straight into OS X.  If I select the Ubuntu boot, it then opens the grub boot menu, with Boot Ubuntu, boot Ubuntu safe (recovery?) mode, memtest, Mac OSX 32 and 64 bit options.

Since I have already chosen to boot to Ubuntu, it would be good to avoid this last menu and go straight to Ubuntu boot. Is this possible?  What should I be looking at changing?

---

### Post by Bucky Ball on 2014-09-12
If you choose Ubuntu and get to the grub menu, can you launch OSX from the option there? If so, might be as simple booting to Ubuntu, opening a terminal, and:

```
sudo grub-install /dev/sda
```

But not a Mac expert and am unsure if it needs to boot from refit or boot camp or something other than grub. The command above would install grub to the MBR of sda and, theoretically, it should boot first. Theoretically. 

Hopefully, someone more Mac-savvy will chime in shortly ...

---

### Post by dcnicholls on 2014-09-12
Thanks.  When I installed Ubuntu, I chose to install grub on /dev/sda3 . I wanted to have equal access to both OS X and Ubuntu.  I found that trying to run either of the grub menu Mac options (32 or (preferred) 64bit) resulted in a crash (though I have not tried this lately), so I thought that either rEFIt or rEFInd should have first call on the boot.  But what rEFIt runs is the grub menu rather than booting Ubuntu, which I would prefer.

---

### Post by Bucky Ball on 2014-09-12
Unsure if that's possible because refit calls the Ubuntu bootloader, not Ubuntu directly, it doesn't actually boot Ubuntu. Think it's supposed to work like that. When you hit the Mac entries in refit, does it go directly to Mac OSX? I'm guessing so.

* Incidentally, this:

>     Make sure to install the bootloader GRUB to your Ubuntu partition (sda# in above the example) and not the master boot record (MBR). 

... from [HERE.]("https://help.ubuntu.com/community/MacBook/TripleBoot#Install_Ubuntu") Also:

> You need to make sure that the boot loader gets installed to your Ubuntu partition and not the master boot record (MBR). 

So scrap my idea of installing grub to the MBR. That would be disasterous! :-k

It appears calling up the Ubuntu bootloader is how things roll. refit is, after all, an EFI boot manager and therefore would call up the bootloaders for each OS installed I'm imagining.

---

### Post by dcnicholls on 2014-09-12
Yes, rEFIt directly loads OS X, but the loads the grub bootloader for Ubuntu.  I can live with it, I just thought there might be a way to make things neater.  

Apart from that, things are working beautifully, now that I have installed and activated the NVidia drivers, and, more important, macfanctld to keep things from overheating.

---

### Post by este.el.paz on 2014-09-12
> **dcnicholls said:**
> I have just installed Ubuntu v 12.04 as a dual boot on my old MBP (5,3) running Snow Leopard.  It works, but the boot process is a bit complicated and I'd appreciate advice on how to make it simpler.  Here's how it goes at the moment:

Settings: I have the following disk partitions:

sda            465.8G            
&#9500;&#9472;sda1 vfat      200M /boot/efi  EFI
&#9500;&#9472;sda2 hfsplus 418.9G            Macintosh HD
&#9500;&#9472;sda3 ext4     37.4G /          
&#9492;&#9472;sda4 swap      9.3G [SWAP]     
sr0             1024M  

[Aside, and probably irrelevant: I had originally set aside a vacant 50Gb on the disk to set up Ubuntu on, but the about Ubuntu map seems to suggest that the Ubuntu install gobbled 50Gb from the existing OS X partition, leaving the vacant disk still empty. OTOH, Disk Utiliy on OS X says all is well, and Macintosh Hard Disk has ~450 GB, with Ubuntu occupying a further ~40Gb and Swap a further 10Gb.  So I don't know which one to believe.]

I have rEFIt installed on OS X (rEFInd seemed to be having problems with the grub menu, so I removed it and installed the older rEFIt,  but I'm not absolutely sure what was going on)

The boot proceeds as follows:

If I turn on the MBP in the standard way, I get the rEFIt menu options that include Ubuntu (two options) and Mac OS (and a few other small buttons for shutdown etc). The Mac option boots as expected straight into OS X.  If I select the Ubuntu boot, it then opens the grub boot menu, with Boot Ubuntu, boot Ubuntu safe (recovery?) mode, memtest, Mac OSX 32 and 64 bit options.

Since I have already chosen to boot to Ubuntu, it would be good to avoid this last menu and go straight to Ubuntu boot. Is this possible?  What should I be looking at changing?

@dcnicholls:

I've got a triple boot on a MBPro . . . so the first comment is, "If it's working, don't 'fix' it" . . . if you are getting both OSX and Ubuntu to "show up and work" then even if there are some "extra steps" . . . be happy, don't worry, etc.  A few responses, from what you're showing from GParted disk utility, there isn't a small partition for GRUB flagged "bio_grub" . . . which may or may not be an issue.  rEFIt is no longer "supported" but does work up to 10.6.8; if you wanted to upgrade OSX you would have to go to rEFInd.  But, for me, the first couple of boots brought the rEFInd window up first, but after that the OSX log in window opens showing "Disk 1" "Disk 2" "Windows" (Xubuntu 14.04) and a "Recovery Disk" . . . I have rEFInd loaded in front of Disk 2, so if I click on Disk 2 I get the rEFInd menu--there I can choose any of the disks/OS I would want (extra step) OR if I select "Windows" it will go through some effort to load the GRUB page . . . it automatically loads "Ubuntu" . . . and on to the Lightdm window . . . .  The process is "not as fast" as OSX, but if it gets there that's a good thing--could it be made "faster"?? perhaps, seems like maybe the newer "amd64+mac" iso's might not need rEFInd and might not need GRUB????  But, I think I have about a "5,3 MBPro" as well, and I've got 14.04 running on it, but, not sure if it will make the next LTS upgrade . . . like I'm saying, having gone through numbers of "problems" getting linux to run on various Mac's if you get a system that works reasonably . . . work with it.

Finally, in terms of the "lost 50 GB" . . . right OSX disk utility might not show any other systems . . . if you chose "Install along side OSX" then the installer "took" the space in OSX and did it automatically . . . .  If you wanted to get that 50GB's back you'd have to re-install and then select "manual" . . . and then use GParted to cut up the 50 GB that you set aside for linux into the three or four partitions  --  bios_grub, ext4, swap. 

e.e.p.

---

### Post by dcnicholls on 2014-09-12
> **este.el.paz said:**
> @dcnicholls:

I've got a triple boot on a MBPro . . . so the first comment is, "If it's working, don't 'fix' it" . . . if you are getting both OSX and Ubuntu to "show up and work" then even if there are some "extra steps" . . . be happy, don't worry, etc. 

Yes, that's what I thought.  In fact, the only excess overhead is one keypress.  Hardly a major problem :-)

>  rEFIt is no longer "supported" but does work up to 10.6.8; if you wanted to upgrade OSX you would have to go to rEFInd.

I don't want to upgrade OS X and in fact, threre's no benefit. My current MBP (mid 2011) is running Mavericks, and Ubuntu v14 Trusty on Parallels (a far simpler set up than dual boot). I had hoped to install Ubuntu v 10 Lucid, because I want to run an application compiled on Lucid.  I'll find out soon enough whether it will work on Precise or Trusty.

> 
Finally, in terms of the "lost 50 GB" . . . right OSX disk utility might not show any other systems . . . if you chose "Install along side OSX" then the installer "took" the space in OSX and did it automatically . . . .  If you wanted to get that 50GB's back you'd have to re-install and then select "manual" . . . and then use GParted to cut up the 50 GB that you set aside for linux into the three or four partitions  --  bios_grub, ext4, swap. 


OS X reckons that things are formatted properly, Not a mjor problem, in either case, as I'm never likely to fill up the disk.

DN

---

### Post by este.el.paz on 2014-09-12
> **dcnicholls said:**
> 

I don't want to upgrade OS X and in fact, threre's no benefit. 

OS X reckons that things are formatted properly, Not a mjor problem, in either case, as I'm never likely to fill up the disk.

DN

@DN:

Thanks for the reply; right, on my '10 MBPro the first disk is 10.6.8 . . . which is perfectly fine as an OS, seems to run the computer "better" than Mav . . . couple less bells and whistles . . . it's the "native" OS, that's why I have rEFInd loaded in front of the second disk (Mav) . . . if I "restart" it automatically loads 10.6.8 . . . if I need to get "complicated" I can hold the option key, etc.

e.e.p.

PS: If your question is "solved" . . . please mark it as such . . . might do something karmic for Bucky B and/or me--thanks.

---

### Post by dcnicholls on 2014-09-13
OS X 'Get Info' report:
[IMG]http://www.dcnicholls.com/misc/disk_data.png[/IMG]

Ubuntu disk utility report:
[IMG]http://www.dcnicholls.com/misc/Ubuntu_disk_data.png[/IMG]

These two agree.  I don't know why the previous method differed.

{looks like the bulletin board is misbehaving, too}

---

### Post by este.el.paz on 2014-09-13
@DN:

Yes, looks like the installer "figured it out" . . . but the OSX "Get info" probably isn't the most accurate measurement, was that from within Disk Utility, or just right clicking?  The first post showing "418GB" is probably more accurate in terms of "what's available" from the "450" . . . because making the partitions takes up large swathes of space . . . .  But, indeed it looks like the ext4 partition was placed in your "50 GB" partition . . . carry on with your "experiments" doctor . . . .

e.e.p.

---

### Post by dcnicholls on 2014-09-13
I ran OS X Disk Utility and the results are similar, though more detailed.  Screenshots for the disk partitions:

OS X: [IMG]http://www.dcnicholls.com/misc/OSX_2.png[/IMG]

Ubunti main: [IMG]http://www.dcnicholls.com/misc/OSX_2a.png[/IMG]

Ubuntu swap: [IMG]http://www.dcnicholls.com/misc/OSX_2b.png[/IMG]

---


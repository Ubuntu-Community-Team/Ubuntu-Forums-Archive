---
title: "Adding New Hard Drive to windows PC...question."
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-04-02
Hi

I'm adding a new hard drive to my Windows PC, which I have 2 SATA WD Raptors in Raid 0. I'm adding a 3rd, SATA drive, where I want to install Ubuntu on.

The Live CD works well on my Windows PC(components listed below), so I thought this might be an easy way, rather than build a whole new system for myself.

Question: When I install to the new drive, Ubuntu will not effect my windows install? also will I get a choice of which OS to boot into at start-up automatically?


ADDING- SATA WD Caviar SE 80GB- for Ubuntu
Intel P4 2.8 skt 478
Abit IC7-G onboard Realtek 5.1 sound
1 GB (4x256) Corsair XMS dual channell DDR400
XFX 6800 GT 256mb
2x WD raptors Raid 0 -72gig
Vantec Ion 450 PSU
Zalman CNPS7000 Copper
Samsung SM-352 CD/DVD combo drive

Thanks,

Gordo

New Windows:

Asus A8N-VM CSM M-ATXw/ Nvidia 6150 graphics and 7.1 HD sound [http://www.newegg.com/Product/Product.asp?Item=N82E16813131570](http://www.newegg.com/Product/Product.asp?Item=N82E16813131570)
AMD Athlon X2 3800+ w/stock cooler
1 GB (2x512) Corsair Dual channell DDR 400
Hitachi Deskstar 120GB SATA II
Aspire X-Qpack Case w/420 watt PSU

New Windows:

Asus

---

### Post by catlett on 2006-04-02
First this is a good non-ubuntu web site how to,  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
The install will not hurt windows. Just make sure when you install you install to your third disc. Linux identifies drives different then Windows. So while the drive might be E on windows, on Linux it might be /hd3. I identify them by their gigabyte size to be safe. The only part of your windows partition that will be touched is the MBR. It will be overwritten by the Ubuntu boot loader Grub. When you boot after install you will see the Grub menu come up and you can choose Ubuntu or XP. 
A couple of things before you start. Make a back up of your XP system. Accidents do happen. It is better to be safe than sorry.Check out the Ubuntu forum main page for the how tos and Wiki guide. Make sure you check that Sata doesn't have a problem. That you understand the limitations of NTFS with Linux. If things get screwed up(this is rare, I'm always installing a second Linux distro to try it out and have no problem with install) you can always get your original MBR(Master boot record) back by booting from your XP install disk(or the recovery disk that came with your computer). Enter recovery mode. When you get to a console enter the command [HTML]fixmbr[/HTML]  That will overwrite Grub and put back the window boot loader. Good luck.

---

### Post by gordong11 on 2006-04-02
Thanks! Perfect!

Honestly I have no need to worry about the NTFS thing(al least I dont think so). I have no need have any link between the OS's, since I"m just keeping this windows system for all my files etc. I will be using a seperate PC for windows use primarily.

I have a monitor that will take 2 inputs, Samsung 172t plat panel..so just need to press 1 button to move between the 2 pc's.

---


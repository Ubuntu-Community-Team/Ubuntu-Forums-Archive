---
title: "Configuring Canon bjc 250 printer"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by gwm on 2006-07-12
**Background**

I have two Windows PCs at home (xp and win98 SE) with a shared bubble jet printer. The cartridge in the printer is black ink only. I have installed Ubuntu on both boxes in a dual boot configuration using Breezy Badger. No fancies, just plain installs. Under Windows, using Open Office 2.03 I can use the printer from either machine and it works well. When I boot up in Ubuntu I get a faint gray-scale-like printout. The printer is configured using the System->Administration->Printing wizard.

**Problems**

1. The only way I can get the second PC to see the printer is when the first PC is booted in Windows and I define the printer as SMB. The networking uses fixed IP addresses. I would like to be able to remove windows from the picture. ](*,) 

2. The faint printing occurs whenever the source of the print job is an Ubuntu box.Printing from Ubuntu yields a very faint gray-scale-like output. The printer configuration is so very different to anything I normally see in Windows and I don't understand it. I've tried fiddling with the settings but whatever I do seems to make no difference. ](*,) 

3. In Windows, the print spooler detects the ink cartridge. Also I'm given three levels of resolution: draft, standard and high. The middle resolution is fine for everyday work and the printer prints at a reasonable speed. When I change to the middle resolution in Ubuntu, the quality is more like draft in Windows. My gut feel tells me that the thing is dithering even though I've turned on black everywhere I can find it in the settings.

There are two entries for this printer that the wizard offers me. These seem to involve the bj600 driver and the gimp-print driver. both give me the same results. I therefore believe that the problem is somehow associated with the settings.

I went to [www.linuxprinting.org](www.linuxprinting.org) and the entry there says this printer is supposed to work well with linux. :confused: 

Does anybody out there know how to get this printer to work properly? I'd appreaciate any help I can get.

gwm

p.s. I've tried to read some of the other discussions on this forum but found I couldn't understand what was being spoken about most of the time. I am still trying to learn linux. Hence the choice of Absolute Beginner Talk. Techie jargon might as well be greek to me at this stage.

---

### Post by gwm on 2006-07-12
I've tried again and have found that I can't make the boxes see each other. i.e. I don't know how to configure the network settings either.

I hope someone can help.
gwm:(

---

### Post by gwm on 2007-02-16
Hi again,
This item can be regarded as resolved.
1. Ubuntu doesn't come with a protocol called SSH installed. One has to install this to get the PCs talking to one another in Linux.
2. I gave up printing from Linux. Recently out of idle curiosity, I tried printing again and it was working fine ?! I don't know what the problem was or what resolved it.:)

---


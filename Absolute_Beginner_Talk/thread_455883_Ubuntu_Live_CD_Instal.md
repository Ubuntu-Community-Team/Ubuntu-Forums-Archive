---
title: "Ubuntu Live CD Instal"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-05-27
I previously posted my installation map for Ubuntu 7.04, and the consensus seemed to suggest I was on the right track. One of the posters suggested I look at Hermanszone for an installation guideline, and it seemed to be quite comprehensive.

But, Herman presents what he says is the opening splash screen from the Live CD, which has as the 1st line "Install in Text Mode". My downloaded Live CD doesn't have this line, it merely states "Start or Install Ubuntu", and either waits 30 seconds, or with a keystroke, loads immediately to the Live CD screen, which has the Instal icon as part of the desktop icon set. When I click this I get the GUI instal procedure.

Part of Herman's website refers readers to the Psychocats site, and when I look there I found the instructions for installing using the GUI setup procedure.

My question is:

I have a primary drive with 2 partitions, one with Windows XP on C:, and data on the other. I want to wipe the data partition and install the partitions /, FAT32 share, and Swap. Is there any advantage to using Herman's guide, which suggests offers more control, or can I use the Ubuntu Install GUI program and achieve the same ends? And will GRUB be loaded using the GUI? If Herman's guide is preferable, does anyone know where I can get the CD that Herman refers to?

I'm getting geared up for this, and want to get the best instal I can. Any suggestions or comments would be really welcomed. Thanks

---

### Post by aysiu on 2007-05-27
The Desktop CD can do everything you want (including Grub being loaded).

---

### Post by southernman on 2007-05-27
> **aysiu said:**
> The Desktop CD can do everything you want (including Grub being loaded).I think he means the Live CD, when referring to the Desktop CD. Pardon me aysui, if I am incorrect here.

---

### Post by hyper_ch on 2007-05-27
Hemran is refering to the alternate install cd...

And you can do what you want BUT I would create a "/", a "/home", a "swap" partition. I would install the ext2/3 drivers in Windows... then windows can write to ext2/3 partition. I wouldn't create an own fat32 for sharing....

Grub will be auto-installed and after installation you will then presented upon boot with different linux options to boot into or windows xp. By default it will be set to the newest linux kernel with a 30 second auto-boot option... however you can alter that.

---

### Post by corowakid on 2007-05-27
> **hyper_ch said:**
> Hemran is refering to the alternate install cd...

And you can do what you want BUT I would create a "/", a "/home", a "swap" partition. I would install the ext2/3 drivers in Windows... then windows can write to ext2/3 partition. I wouldn't create an own fat32 for sharing....

Grub will be auto-installed and after installation you will then presented upon boot with different linux options to boot into or windows xp. By default it will be set to the newest linux kernel with a 30 second auto-boot option... however you can alter that.

Excuse my ignorance, but what are ext2/3 drivers in Windoze, and how does one instal them? Are they on the Live CD? Sorry if its a dumb question, but a newbie like me most times finds the level of conversation excaping me because I'm not familiar with Linux enough yet.

---

### Post by southernman on 2007-05-27
> **corowakid said:**
> Excuse my ignorance, but what are ext2/3 drivers in Windoze, and how does one instal them? Are they on the Live CD? Sorry if its a dumb question, but a newbie like me most times finds the level of conversation excaping me because I'm not familiar with Linux enough yet.
It's just a program that allows dual booters to be able to read/write to their linux installation, from windows.
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by nickpaton on 2007-05-27
Hi and welcome once again to Ubuntu and the forums!

I've read through your previous posts and understand your confusion, though the replies given are 100% in the right direction for you.

What Herman is suggesting you do is to use the Alternative Installation CD rather than a Desktop one.
A good explanation of the differences can be found on the Psychocats site [here]("http://psychocats.net/ubuntu/whichbuntu"), and scroll down to the sectiion entitled "Desktop CD, Alternate CD, or Server CD?"

For me personally I can run the Desktop CD without any problems and I would suggest if you have already downloaded one onto a CD to give it a go and see what happens.
Psychocats gives a good step by step[ here]("http://psychocats.net/ubuntu/installing").
Remember with a desktop CD initially you are simply loading Ubuntu into RAM and not installing it, so you have nothing to lose by doing that. It doesn't have the potential to damage any other program so to speak!

If you want to use the Alternative Install CD, go [here]("http://www.ubuntu.com/getubuntu/downloadmirrors").

Then select your country (I'll give an example for mine - the UK) and go to 7.04 [here]("http://www.mirrorservice.org/sites/releases.ubuntu.com/7.04/") if you want Feisty.

You will see that* ubuntu-7.04-alternate-i386.iso* is listed and click to download as usual.

I would also go with the suggestions made in your other post to install on the same HDD as your Windows and to use the externall HDD as common storage for both distros - much easier.
Also if you use Alternative CD, make sure you say Yes to installing GRUB on your Windows MBR as per Hermans at section fig 35 fat.

HTH and good luck!

---

### Post by corowakid on 2007-05-27
> **southernman said:**
> It's just a program that allows dual booters to be able to read/write to their linux installation, from windows.
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

Well, I ask and you give me exactly what I was looking for. Many thanks.

---

### Post by hyper_ch on 2007-05-27
btw, reading data from your ntfs drives can also be done by default from ubuntu... however writing to them will require to install the ntfs-3g drivers... those are, by some considered, not as stable and if anything goes wrong, then you may loose all your data on your ntfs-drive...

---

### Post by southernman on 2007-05-27
> **corowakid said:**
> Well, I ask and you give me exactly what I was looking for. Many thanks.That's what the good book says too.... "Ask and ye shall receive."

Apologies to you and any others reading that, which may be of a different faith.

I'll add that ext2 is an older type of file system, ext3 is (at least from what I've read and heard at local Linux User Group meetings) the better choice. The link I gave you was just the first one from my Google search.

Apologies to the OP for straying off topic.

[edited]Thanks hyper_ch for reverse engineering the scenario... ;) [/edited]

---

### Post by hyper_ch on 2007-05-27
Well, Ext2 doesn't have journaling as Ext3 has... but those Ext2 drivers can access Ext3 partitions from windows :)

---

### Post by southernman on 2007-05-27
ah... ok. I thought both were journaling. TY

---


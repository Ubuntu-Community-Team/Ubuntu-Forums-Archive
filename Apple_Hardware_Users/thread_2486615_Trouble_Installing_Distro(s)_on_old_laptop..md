---
title: "Trouble Installing Distro(s) on old laptop."
date: 2023-05-05
forum: Apple Hardware Users
---

### Post by sali1001 on 2023-05-05
Hi everyone!

So I'm currently on a long vacation. I work remotely and independently. The other day my machine got stolen. I'm quite remote at the moment so a friend gave me his old MacBook (the last 17 inch MacBook Pro).

It's really old and slow so I decided to install Linux onto it but have run into consecutive problems. Its an old MacBook so I used a command line tool called Diskutils to burn the ISO onto a USB. 

For Lubuntu and Linux Mint: 
The ISO successfully burned onto the USB but when I boot the machine up there is no option to boot from USB.

For Elementary OS: 
The machine can successfully read the USB as bootable but when I continue with the installation I get a black screen. I recognize that many people have this problem with elementary but I've tried the solutions (editing grub file) to no avail.

I'm at my witts end, I've spent the last day and a half doing this. I'm not sure if I'm posting in the right place. But can anyone assist me on either point?

---

### Post by QIII on 2023-05-05
Moved to Apple Hardware Users sub-forum to get this seen by the right people.

You might want to give more specifics about your machine, including something close to the year it was made and the hardware specs.

---

### Post by guiverc on 2023-05-05
The ISO9660 format is a very large *'standard*' allowing a lot of variation in how ISO files are created, and then need to be written correctly for the type of ISO you downloaded... why each distribution of GNU/Linux, Windows & BSD have guidelines & for some tools that write the ISO correctly to media.

You didn't provide specifics as to releases; mentioning for Elementary worked by two others didn't; which may just mean you used a write method that was good for a Elementary but not the others, but you gave *few* specifics as to how it was written.  Did you try reading [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)

You also gave no release details; Ubuntu 20.10 & later media varies in how its booted; as Ubuntu now spends energy ensuring a given release boots the same regardless of architecture for a specific release; thus release matters (*and some ISO writes of 20.10 & later won't work with older software tested intended for  20.04 & earlier for example*).  FYI:  The method covered in the tutorial works for all releases if the software was fully-updated.

I don't know Mac hardware, nor the software you mention, but I'd follow the specific rules for the given product & release you're trying to use & for the *unstated* release of that product. I'd also suggest providing that detail if you are hoping for specific help.

(You mention Lubuntu; with *live* and non-*live* ISOs currently available for download [from cdimage.ubuntu.com], using three different installers selected by the ISO you download, but you gave no specifics as to what you tried.  Did you verify the ISO after download? to ensure it was correct; if you're sure the write to thumb-drive was perfect, I'd use another device to perform the (*thumb-drive*) media verification (*this doesn't require install or any changes; you're just using the other device to boot the live system (assuming it's a live ISO) to 'try' and ensure the write was appropriate & correct for the ISO & method you used to write*; *but I have little experience with ISOs written for macs*).

---

### Post by sali1001 on 2023-05-05
For each ISO I just downloaded the latest release. I verified each. It is an old MacBook. I erased and unmounted the disk each time.Then I used a command line Mac program called diskutils. Like I mentioned the mac is old so using third party software to burn the ISO has not been succesful. 

Specifically the command I used was: **dd if=./linuxmint-21.1-mate-64bit.iso of=/dev/disk1 bs=1m** to write to the USB. 

I will take a further look ino what you mentioned/ thank you

I should also mention that I have been only trying lightweight versions of Ubuntu as the machine is quiet old.

---

### Post by guiverc on 2023-05-06
All Ubuntu ISOs (*include flavors*) should work if you just **dd** or *clone* the ISOs to thumb-drive.

Terms like *latest* make me nervous... With Lubuntu, our latest is 20230505 for *mantic* and *jammy *(ISOs all have a date in format YYYYMMDD), but you probably mean a released ISO where we offer many (*latest would be lunar/23.04 which is 20230417 for Lubuntu, or              20230217.1 for jammy/22.04.2*) but which do you mean??  Providing release is always helpful.

The web site you go to also matters, eg. I can go look at the [Lubuntu *official* site]("https://lubuntu.me/downloads/") and know what is offered for download, but I'm also aware that some just ask google for a Lubuntu site and thus can get directed to a *fan* or *fake* site which also offers downloads of something that may or may not come from Ubuntu/Lubuntu.. 

I don't know your device, but some quick searches online for specs reminded me of a device I use in QA of Lubuntu (*and like*), which is *lenovo thinkpad sl510 (c2d-t6570, 2gb, i915)*. If using Qt5 apps Lubuntu will be lightest, however if using GTK3 apps I'd suggest Xubuntu.

---


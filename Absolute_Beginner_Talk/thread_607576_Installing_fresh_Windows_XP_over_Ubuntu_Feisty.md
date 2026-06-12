---
title: "Installing fresh Windows XP over Ubuntu Feisty"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by aek5k on 2007-11-09
This may sound like a strange problem, but I am trying to re-install windows xp over ubuntu but when I boot up the setup disc it says that it cannot recognize any harddrive in the computer. I am using an IBM thinkpad x60s with ultrabay dock if that helps any.

---

### Post by Daveth on 2007-11-09
it is probably getting upset by bumping into ext3 rather than fat32 or ntfs. You could do no better than use Gparted from a live Ubuntu CD, and format and re-size the partitions, then putting XP back, assuming you are starting over and do not mind the hard drive contents getting trashed.

---

### Post by cybson on 2007-11-09
... or it might be that you need SATA-drivers for your harddrive since XP has none in it's original state.

---

### Post by hyper_ch on 2007-11-09
my vote goes to cybson.

You'll need to get the sata drivers and put them on a floppy and while starting the winxp routine you can press a key to search for sata drives in the floppy drive.

Or you could slipstream a windows copy and include the sata drivers...

---

### Post by Dripbagulhos on 2007-11-09
> **hyper_ch said:**
> my vote goes to cybson.

You'll need to get the sata drivers and put them on a floppy and while starting the winxp routine you can press a key to search for sata drives in the floppy drive.

Or you could slipstream a windows copy and include the sata drivers...

In the begining of the boot process of Windows XP (from the cd) you will get a blue screen, in whutch you could see something like this "Press F6 if you want to install third part drivers". At this point you have two choises:
1) prepare a floppy with the driver for SATA or PATA controler, then just insert is on the floppy drive, or, if you doesn't have any floppy (my case, eheheh)
2) remaster the Windows XP cd with nLite ([http://www.nliteos.com/](http://www.nliteos.com/)). It is a windows program, very simple that permits to insert drivers (and a lot of extra things) on the cd. At the end of the process you will finish with an ISO image ready to burn.

---

### Post by aek5k on 2007-11-09
Thanks for all the help, can anyone possibly walk me through the process of adding SATA drivers via slipstream or nlight on Ubuntu?

---

### Post by hyper_ch on 2007-11-09
have a look at the nlite website as posted by the previous poster.

---

### Post by aek5k on 2007-11-09
I understand how to use it on windows, but the problem remains that I do not have windows installed on my laptop, only ubuntu. Is there a linux alternative or way to use it on linux?

---

### Post by Dripbagulhos on 2007-11-10
> **aek5k said:**
> I understand how to use it on windows, but the problem remains that I do not have windows installed on my laptop, only ubuntu. Is there a linux alternative or way to use it on linux?

You can install the VMWare Server 1.04 (it's free of charge) and then install Windows XP on it, then follow the intructions of nLite.

See this tutorial about installing VMWare Server:

[http://www.ubuntugeek.com/how-to-ins...sy-gibbon.html](http://www.ubuntugeek.com/how-to-ins...sy-gibbon.html)

---


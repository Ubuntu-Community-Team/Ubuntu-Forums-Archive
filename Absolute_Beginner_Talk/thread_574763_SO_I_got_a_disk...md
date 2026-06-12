---
title: "SO I got a disk.."
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by TaiQui on 2007-10-13
I have a windows vista disk, and ubuntu automatically opens it and there are 4 folders

BOOT, EFI, SOURCES, and then a file named: BOOTMGR


It doesn't start automatically though. Any Help, please?:confused:

Thanks,
TaiQui

---

### Post by Tomosaur on 2007-10-13
> **TaiQui said:**
> I have a windows vista disk, and ubuntu automatically opens it and there are 4 folders

BOOT, EFI, SOURCES, and then a file named: BOOTMGR


It doesn't start automatically though. Any Help, please?:confused:

Thanks,
TaiQui

Why would it start automatically? As far as Ubuntu is concerned the disk is just a disk with some files on it. I would imagine you need to reboot the machine with the disk inserted to get it to 'run'. To do this, ensure that your BIOS is set to boot from the CD drive first (the method of doing this will depend on your particular BIOS / Motherboard, so just reboot your computer and look carefully for something along the lines of "Press F2 to enter setup".

---

### Post by TaiQui on 2007-10-13
Ok, I'll try.

EDIT: I need to format to NTFS. Theres always an error when I do it through the disk, so is there any programs for this?

---

### Post by TaiQui on 2007-10-13
bump

---

### Post by Martje_001 on 2007-10-13
You can partition your disk with GParted.
```
sudo apt-get install gparted
sudo gparted
```

---

### Post by TaiQui on 2007-10-13
I installed it, and Add/Remove says its in my menu, in system tools, but there is no system tools on my apps menu.

---

### Post by Tomosaur on 2007-10-13
> **TaiQui said:**
> I installed it, and Add/Remove says its in my menu, in system tools, but there is no system tools on my apps menu.

Isn't there a 'System' menu, seperate from the 'Applications' and 'Places' menu?

Are you using normal Ubuntu, or some other variant, such as Kubuntu or Xubuntu? If you're using the normal version, then the top panel should have a 'System' menu.

---

### Post by Dr Small on 2007-10-13
You can run gparted by opening either the terminal or ALT + F2 and typing,
```
gksudo gparted
```

By the way, it should be under System > Administration > Gnome Partition Editor.

Dr Small

---

### Post by TaiQui on 2007-10-13
Oh, ok, I didn't know it'd be in there. Thanks!

Edit: So, I opened it. How exactly do I format it now?

---

### Post by Martje_001 on 2007-10-13
I think you want to split the disk up, so you can keep ubuntu? Well, in that case:

1. Boot up from live-cd
2. Install Gparted
3. ALT+F2 --> sudo gparted
4. resize to a size you want

reboot.
Make sure you make a backup and you place you windows partition AFTER linux!

---

### Post by American_Outcast on 2007-10-13
I am a bit lost. What exactly are you trying to do? Resize or create a partition and install Vista on a that NTFS partition?

---

### Post by Dr Small on 2007-10-13
> **Martje_001 said:**
> I think you want to split the disk up, so you can keep ubuntu? Well, in that case:

1. Boot up from live-cd
2. Install Gparted
3. ALT+F2 --> sudo gparted
4. resize to a size you want

reboot.
Make sure you make a backup and you place you windows partition AFTER linux!
Gparted comes by default on ubuntu live cds, so no need to install it.

Dr Small

---

### Post by American_Outcast on 2007-10-13
> **Martje_001 said:**
> I think you want to split the disk up, so you can keep ubuntu? Well, in that case:

1. Boot up from live-cd
2. Install Gparted
3. ALT+F2 --> sudo gparted
4. resize to a size you want

reboot.
Make sure you make a backup and you place you windows partition AFTER linux!

Martje covered where I was going with my previous reply. Just make sure your write down on a separate piece of paper what the partitions are for future reference. For example for Ubuntu maybe its something like, /hda/ for swap and hda2 for root and hda3 for NTFS where you would install Vista...... Of course those are examples, your partitions may be set up completely different. My point is keep track of what you are doing, what partition is what and remember once you make changes, or mistakes, to it there is no turning back.

---

### Post by Martje_001 on 2007-10-13
Maby you can make a screenshot of gparted and give us a look?

---

### Post by TaiQui on 2007-10-13
[IMG]http://i23.tinypic.com/1zfikwl.png[/IMG]

What I want to do is install vista over ubuntu because befoe I acciddently installed ubuntu over windows and didn't create a seperate drive. Next time I am going to use wubi to dual boot with ubuntu.

---

### Post by Martje_001 on 2007-10-13
> **TaiQui said:**
> [IMG]http://i23.tinypic.com/1zfikwl.png[/IMG]

What I want to do is install vista over ubuntu because befoe I acciddently installed ubuntu over windows and didn't create a seperate drive. Next time I am going to use wubi to dual boot with ubuntu.
The 'lock' says you're not running from the live-cd (or the hdd-disk is mountend), you have to if you want to resize!!!.
You have to rightclick on 'ext3' and resize it.

And btw. I don't think it's ubuntu's fault it didn't created a seperate partition, I think you clicked 'use entire disk'.

---

### Post by American_Outcast on 2007-10-13
If you are doing a clean install of both Vista and Ubuntu then I recommend this,

sda1 for vista, formated as NTFS

(Ubuntu)
sda2 for swap 
sda3 for / formated as ext3
sda4 for /home formated as ext3

Choose the sizes you prefer for each partition. (Of course you will have to do this with the Ubuntu livecd.)

---

### Post by TaiQui on 2007-10-13
When I tried to format the drive on live CD I got this:

[IMG]http://i21.tinypic.com/a2cbq1.png[/IMG]

The error was:

could not open /dev/sda1 : Device or resource busy.

---

### Post by TaiQui on 2007-10-13
bump

---

### Post by TaiQui on 2007-10-13
Could someone please help? now I have a huge error, It doesn't have any file system and I still can't boot windows.

---

### Post by American_Outcast on 2007-10-13
Are you redoing the whole disk?

If so then go into the terminal and type sudo cfdisk /dev/sda.

Try it that way, but only if you are formatting the whole disk, you will loose all data. After then then try gparted on the livecd.

---

### Post by TaiQui on 2007-10-13
Yes. I'll try that

---


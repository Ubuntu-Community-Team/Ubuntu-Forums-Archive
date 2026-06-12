---
title: "Install ubuntu partition problem"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by stigmatist on 2008-02-20
Hi everyone,
I will be an Ubuntu user if I can achieve to install it.
I am using XP pro with service pack3 in my computer. I have 80 Gb HDD and three partitions of 35GB 25GB and 20GB. I wanted to install Ubuntu to my 25GB partition and keep also XP.

Howver all of my trials during the installation end up with collapse of my existing operating system, and I am at the edge of giving up trying to learn Linux.

I tried various things. I formatted the partition that I want to install ubuntu as FAT, FAT32, ext2 and ext3 by using partition magic. However when I turn to the installation, Ubuntu cannot see my partitions. Once I had my external Harddisk connected to my computer during installation and Ubuntu detected my external HDD and asked to install in it. My external HDD is in FAT32 format.

Partition MAgic has a tool inside that you can arrange a partition for another operating system. I tried this tool and selected Linux as the 2nd operating system. It formatted the selected 25GB partition as ext2. When I pressed the apply changes button the computer restarted and arranged the new partitioning. However my computer did not open and give an error of `Error loading operating system`. I lost my XP and cannot install Ubuntu.

Any idea?????
Please help.

---

### Post by hyper_ch on 2008-02-20
Do this:

(1) Start Partition Magic

(2) Delete that partition that you don't want anymore

(3) Leave that space UNPARTITIONED

(4) Start the ubuntu installed and select "Use largest continouuse empty space" (or something like that). DO NOT USE "USE ENTIRE DISK".

--> Ubuntu will the partition that empty diskspace (the 25 gb) according to what it thinks is best and install it there. It will not harm your windows installation.

(5) After partitioning you are asked whether you want to have GRUB installed (at least on the alternate install). Select YES.

---

### Post by jan quark on 2008-02-20
Partition magic is known for being very ... searching the right word... very problematic

just make a blank partition, no format type, just blank free space

and install Ubuntu on this partition.

Ubuntu can handle the format process by itself, during the installation process with the tool gParted.

your windows is probably still there but somehow partition magic managed to screw your boot loader.

you can boot from the Ubuntu live cd and check if your windows partition is still there with the command

```
sudo fdisk -l
```

and you can use the super grub disc to restore the boot loader
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

these are just general suggestions,
someone other might perhaps concrete solutions

---

### Post by stigmatist on 2008-02-20
Thanks for your quick reply I will try this method tonight. In tried this also, made an unpartitioned part but when I begin  with installation Ubuntu again cannot find the partition. I will try `Use largest continouuse empty space` thing tonight I hope it will work.

I downloaded Ubuntu 7.10 from the Ubuntu website nad burned into a CD with the help of UltraIso program and used this in the installation. Can this cause a problem?

Installation starts I select the installation language then regional configurations came after these, installation looks for some partition but cannor find.

I did not mention about the installation procedure so did I now. May be the problem about one of these steps.

Thank You.

---

### Post by Duck2006 on 2008-02-20
This may help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Paqman on 2008-02-20
> **stigmatist said:**
> 
I downloaded Ubuntu 7.10 from the Ubuntu website nad burned into a CD with the help of UltraIso program and used this in the installation. Can this cause a problem?

If you're worried that you might have burnt a bad disk then there's an option when you first boot the LiveCD to check the disk for errors. It takes a while to complete.

> 
Installation starts I select the installation language then regional configurations came after these, installation looks for some partition but cannor find.

Are you able to boot up to working desktop with the LiveCD? If so, try running the Gparted tool. You'll be able to see what partitions Ubuntu can see, and whether they have any problems. I'd recommend always using Gparted to change your parititions, instead of Partition Magic.

---

### Post by Bartender on 2008-02-20
I would download/burn a copy of GParted LiveCD, or the combined Clonezilla/GParted CD that's now available.

gparted-livecd.tuxfamily.org isn't responding this morning... :(

If you want to take a screenshot and post it to the forum so we can see what you've got, it's easier to do that with the partitioner on the Ubuntu LiveCD because "Take Screenshot" is right there in the Applications>Accessories menu.  It's easy to plug in a thumb drive after you have the LiveCD running, check on the desktop to see that it's recognized, then save the screenshot to the thumb drive.

But for actual partitioning the GParted LiveCD is more reliable. 

I've had problems before when trying to install to an unformatted partition.  Ubuntu/Xubuntu/Kubuntu sometimes doesn't recognize it and doesn't know what to do.  I don't think I've ever had a problem when I formatted the partition as ext3 first.  Even if you auto-install.  Ubuntu will just take part of that partition and reformat it for the linuxswap.

Try using GParted LiveCD to format to ext3 first, then go back with the Ubuntu LiveCD or alternate install CD.

---

### Post by Duck2006 on 2008-02-20
Or you can use pmagic

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by stigmatist on 2008-02-20
I tried to leave the space that I want to install ubuntu unpartitioned. However it still did not work. I used ubuntu partition editor to see the partitions of my computer, however GParted cannot find any installed device and there is nothing.

Also there is not a choice as install ubnutu to largest continuous space or such a thing. In fact there is not any choice about anything. When my computer is booted over CD a menu appears that includes install Ubuntu option. When I selected install ubuntu, ubuntu starts as if it already installed on my computer. There are two icons on the desktop one is Examples folder and the other one is Install file. When I clicked to the install, it asks installation language and region and then it checks for the available partitions and again cannot see nothing. Sorry I couldn`t be able to take screenshots therefore I tried to explain every detail. 

I am now using Ubuntu and writing this message. Ubuntu now works on CD and I can connect to the internet. I did not understand the solution about using Gparted Live CD.

---

### Post by stigmatist on 2008-02-20
For example I did not see a window like in the link below never:
[http://img379.imageshack.us/my.php?image=feistydual06rw5.png](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)

---

### Post by Moop on 2008-02-20
Since you have the live cd working let's see if your hard drive is showing up. Go to System-Administration-Partition Editor. That should show you your hard drive and the partitions on it.

What version of Ubuntu are you trying to install?

---

### Post by stigmatist on 2008-02-20
When I go to Partition editor, GParted starts but there is nothing but a message under the window that no devices are detected.

I am trying to install Ubuntu 7.10.

---

### Post by Moop on 2008-02-20
I don't know why your hdd isn't being detected but obviously you need to solve that problem before you can install Ubuntu. 

Maybe try plugging it in a different port on your motherboard or trying a new cable. If XP is working then your hdd must be showing up in the bios.

Gparted has a live cd you can boot from. If that is able to see your hdd then you must have a bad Ubuntu live cd. 

[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

---

### Post by stigmatist on 2008-02-20
I downloaded Ubuntu iso file and write to the Cd by using UltraIso. Does this cause a problem related with the CD?

---

### Post by Moop on 2008-02-20
> **stigmatist said:**
> I downloaded Ubuntu iso file and write to the Cd by using UltraIso. Does this cause a problem related with the CD?

That should work fine. It's best to burn the cd at the slowest speed to avoid errors. Have you checked the cd for errors? You have that option when you boot.

---

### Post by stigmatist on 2008-02-21
I will try this again tonight after work. Thanks for your help. For about one week I have been dealing with this problem and I am almost done.

I think I have to find someone that knows about linux and ubuntu and show the problem. I will ask my friends in university.

---


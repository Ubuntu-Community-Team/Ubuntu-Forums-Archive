---
title: "HDD got corrupted...."
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Space Cowboy on 2006-11-20
I bought a gateway laptop a while back and it came a windows recovery partition instead of a real install cd. I had successfully dual booted windows and ubuntu up untill a few weeks ago when my whole HDD got corrupted somehow... Im still not sure how but whatever, **** happens. 

After this my windows recovery partition was screwed, but I have a couple of regular windows install disks. I tried both of these, but neither of them detected my HDD, so I figured hey, I have been mainly using Ubuntu for the past few weeks, I don't need windows anymore. I was pretty much right, I haven't needed windows for much, and what I did, wine and VMware have sufficed. 

But now I kinda miss windows on this laptop, I would like to dual boot again, but my windows disks still don't detect my HDD. I assume there is some way to fix this. I would love to keep my Ubuntu install I have right now I have been using it for weeks and its configured just how I like it, it would take a while for me to get a fresh install back to how I like it.

So what would you guys suggest I do so that my windows disks detect this HDD, I can install windows, and still preserve (I will have to resize it) the Ubuntu partition.

---

### Post by jaboua on 2006-11-20
You might need to load some harddrive drivers during the windows install. If you have these drivers on a driver CD, I believe there is a way to tell the windows installer to load them before trying to detect disks - but I've never done that myself, and unfortunately can't help you with exact instructions. If I remember correctly, the windows installer will tell you when the time is right to load third party drivers (was it for RAID and SCSI the installer said or something like that?), it's like a 5 second limit or something during the initialization of the installation CD.

---

### Post by Space Cowboy on 2006-11-20
Well I'll look into that but prior to the time this drive was corrupted, I installed win2k on a 10gb partition and didnt need to load any drivers...

Do you think anything like Partition Magic or Acronis could do the job?

---

### Post by smoker on 2006-11-20
i think jaboua means sata drivers, you shouldn't need these for your laptop,

the windows install disk wont recognize the linux file system so you will probably have to partition your harddrive and format one partition as fat32 or ntfs, you should then be able to install windows to that partition.

But! i am not sure how this will go as to dual-booting between windows and ubuntu. normally you would install windows first, and then unbuntu, and ubuntu sets up grub for dual-booting. maybe someone with more knowledge about this could comment in more detail,

partition magic or acronis maybe do the job, but on the ubuntu cd you have gparted  which would probably be easiest.

---

### Post by NiklasV on 2006-11-20
First of all, remember to make a boot cd in order to boot and restore grub later, the windows installation process wil overwrite your MBR.
You can use the super grub disk ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) to restore GRUB after the windows installation.

You can use gparted to resize your ubuntu drive and make a fat32 or ntfs partition in the freed space. (I would recommend fat32 since the kernel has built-in write support for that file system)
Don't do this while in Ubuntu, the partition you're resizing will have to be unmounted. You can either use the Ubuntu live cd or the gparted live cd ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))

Install Windows as usual, loading SATA/other drivers if necessary.

Boot from the super grub disk and restore GRUB.

---

### Post by Space Cowboy on 2006-11-21
Thank you, I will do this, one question though, I know I can use the ubuntu cd though gparted on the live cd is out of date, but I tried the gparted live cd and it doesnt detect my disk so I have to load the modules, but I am not sure which one, there are so many. My drive is a Serial ATA FUJITSU MHV2120B. I know its SATA but, I am not sure which module to load, I have never come into a situation where I needed to know that so, yeah I'm not sure... I would like to know how you tell what module you need for future reference...

Thanks for the help.

---

### Post by gn2 on 2006-11-21
Think you need a W2kPro disc to have ServicePack 4 included before you can install it to a SATA drive.

---

### Post by smoker on 2006-11-21
> i think jaboua means sata drivers, you shouldn't need these for your laptop,

ah, sorry, didn't realise this was a sata drive, you should be able to copy the correct sata drivers from your original drivers disc supplied with the laptop, normally these should be copied onto a floppy and when windows install starts, shortly after you will be asked to press f5 or f6 to install additional drivers, at that stage press the function key and insert floppy.

if your laptop dosent have a floppy drive, maybe you can load the drivers some other way, you may have to read the documentation for this, or consult the gateway website.

---

### Post by Space Cowboy on 2006-11-21
I said already, this is a gateway laptop, as you know gateway doesnt include a driver disk or a windows install disk, it came with only a recovery partition and a disk to activate that, but the recovery partition was wiped, so yeah...

Although as I have stated, both of the windows install disks I have detected this SAME drive before it was corrupted, and I didnt need any extra drivers to install. I have a copy of Win2k advanced server and WinXP pro sp2, and I successfully installed win2k on a 10gb partition, it detected the drive, and didnt need any drivers. Since this PC didnt come with a drivers disk I do not have one, but I will deal with that later, though I may not have to.

What I need to know now is how you tell what modules to load on the gparted live cd. Once it comes to the part where you load extra modules, it says sata/scsi, I go under here but there are a ton of sata_* modules. I guess I could go trial and error but I know there has to be a way to tell which one you need...

Again, thanks for the help.

EDIT: There may be drivers on this CD that activates the recovery partition, I will check it out...
EDIT2: Yeah there are a ton of .sys files... not sure which ones or how to load them but I'll figure that out...

---

### Post by smoker on 2006-11-21
hi, about the gparted, i've never had to choose any modules, i've always just  pressed enter at at options highlighted and it has always worked for me, maybe i've just been lucky tho,

sorry about the gateway probs, i never deal much with laptops, so am not an expert in this field,

---

### Post by Space Cowboy on 2006-11-21
Thats what I am saying, I have never had to choose any modules to load, I know there has to be a way to tell what you need, but I have never needed to in my experience with linux, it has always installed fine and then I get my work done.

---

### Post by Space Cowboy on 2006-11-21
Ok, I resized my linux partition with the Ubuntu Live CD since I still dont know what module I should load, now Im just working on getting windows to detect my disk. I have an unformatted portion about 66bg, im only going to make my windows partition 45 gb, and the rest data, but Windows still doesnt detect the HDD, Im going to update my gparted at the moment because I cant get the one on my ubuntu install (not off the live cd) to work, it keeps having errors...

---

### Post by gn2 on 2006-11-21
If you have access to a desktop PC, your easiest cure should be to use it to delete all partitions on the drive then install Windows to the unallocated space.
Windows will create partitions and format as required during install.
You could use this (free demo) partitioning tool to delete the existing partitions: [http://www.vnunet.com/vnunet/downloads/2167398/paragon-partition-manager-2005](http://www.vnunet.com/vnunet/downloads/2167398/paragon-partition-manager-2005)

---

### Post by Space Cowboy on 2006-11-21
> **gn2 said:**
> If you have access to a desktop PC, your easiest cure should be to use it to delete all partitions on the drive then install Windows to the unallocated space.
Windows will create partitions and format as required during install.
You could use this (free demo) partitioning tool to delete the existing partitions: [http://www.vnunet.com/vnunet/downloads/2167398/paragon-partition-manager-2005](http://www.vnunet.com/vnunet/downloads/2167398/paragon-partition-manager-2005)

I have a windows desktop I can use, and I have partition magic on there, but how would I do this? I have a crossover cable to network them, but how would that work?

Also the part thats not partitioned (it shows up as unformatted gray in gparted) isn't that unallocated?

---

### Post by gn2 on 2006-11-22
> **Space Cowboy said:**
> I have a windows desktop I can use, and I have partition magic on there, but how would I do this? I have a crossover cable to network them, but how would that work?

Also the part thats not partitioned (it shows up as unformatted gray in gparted) isn't that unallocated?

Remove the drive from the laptop and connect it to the other PC, easiest done with an external USB enclosure.

Never used Gparted myself (I also have Partition Magic), but grey bit could perhaps be a hidden partition?

---

### Post by Space Cowboy on 2006-11-22
> **gn2 said:**
> **Remove the drive from the laptop** and connect it to the other PC, easiest done with an external USB enclosure.

Never used Gparted myself (I also have Partition Magic), but grey bit could perhaps be a hidden partition?

No thanks. This drive doesn't just slip out, and I'm not taking apart this laptop or buying extra hardware. I'll just make a slipstream windows install disk with my drivers integrated. 

Also when I referred to that gr_a_y area, I knew exactly what it was, its unallocated hard disk space that has no format. I don't see why I would need to use my desktop to do something thats already done... 

I really have no Linux problems any more, this is all Windows issues so yeah theres no more point discussing it here, I'll bring it up at another forum if I need any more assistance.

---

### Post by gn2 on 2006-11-23
> **Space Cowboy said:**
> No thanks. This drive doesn't just slip out, and I'm not taking apart this laptop or buying extra hardware. I'll just make a slipstream windows install disk with my drivers integrated. 

Good luck with the slipstream process.......

> **Space Cowboy said:**
> Also when I referred to that gr_a_y area, I knew exactly what it was, its unallocated hard disk space that has no format. 

Not according to your last post you didn't  

> **Space Cowboy said:**
> I don't see why I would need to use my desktop to do something thats already done...

Because it's better to use Partition magic than gparted Live CD?

> **Space Cowboy said:**
> I really have no Linux problems any more, this is all Windows issues so yeah theres no more point discussing it here, I'll bring it up at another forum if I need any more assistance.

Strangely enough this forum has been a fountain of Windows knowledge for me, and it's friendly too.

Good luck with the W2kPro install, it's my preferred flavour of Windoze and works a treat.

---


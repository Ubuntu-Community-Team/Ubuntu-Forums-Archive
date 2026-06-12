---
title: "boot raid 1 store raid 5"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by rgotten on 2008-04-06
Finally i am ready to install ubuntu server edition and even though the motherboard is raid enable evidently is a fakeraid and will not work under ubuntu. After researching is my impression the the sofware raid will work well and even sometimes it is better than the hardware and less expensive. This is my question in the event i need to buld from a crash ( i will still make backups of the server), But in regards to the raid this are my questions:

Originally i was going to do a raid 5, but then reading all over the internet found that i should have to do boot in raid 1 and the rest for storage in raid 5, so if the boot section is damage i can still boot up. I have (3) 500 gb hd then:
a) how big should the boot partition be for the raid 1? 
b) Since i have the 3 hard drive, should i have the same boot partition areas on each of this 3 hd? and can this 3 partiton be on read 1 
c) can i have raid 1 in this 3 equal size partitions, and then do the rest of the partition for each one of the hd for the raid 5 so evrything is on equal sizes?

Remember i am completely new to Ubuntu server, and instructions will be well apreciated
:confused:

---

### Post by dstew on 2008-04-07
> a) how big should the boot partition be for the raid 1? It only needs to be about 100 Mb (megabytes) because it contains only the boot configuration files and the kernel(s).> Since i have the 3 hard drive, should i have the same boot partition areas on each of this 3 hd?Yes, I would make a 3-disk array for the RAID1, to be mounted on /boot.> c) can i have raid 1 in this 3 equal size partitions, and then do the rest of the partition for each one of the hd for the raid 5 so evrything is on equal sizes?
Yes, make the rest of the disks into a RAID5, mounted on '/'. You might also want to make a swap partition on the RAID5.

Use the Alternate Install CD to create and install to the RAIDs. It is hard to do using a Live CD.

---

### Post by rgotten on 2008-04-07
Thanks for your answer. I am new to all this and let me go deepr into my original question.

Originally i was going to do Raid 1 and the guys at tiger direct (were i bouth the parts for my server) recomended me a Raid 5 since if one of the 3 hard drive fails, teh system will keep on working. Then I read that in order to do Raid 5 i should have a the boot part on Raid 1 so it is morrowed and can boot after a crash. 

This are my new questions after mentionning the above:

Should i just make a 2 hard drive Raid 1 and return one of the hard drive or should i make like you told me raid 1 into the boot area for each one of the 3 hard drives and then the rest 490 gigs on raid 5 for storage, and I am complete new onto this, what is the meaning of a swap partition, and what and were can i do the alternate CD.

Any way to get insturction where can i get this and follow them, your help is rally appreciated

Rgotten

---

### Post by dstew on 2008-04-07
RAID-5 needs at least 3 disks. The bootable RAID-1 partition is so small, you can just make it a thin slice of your other disks, it won't take up very much space. With software RAID, you can take partitions from the same disks, and make a RAID-1 out of some, and a RAID-5 out of the rest. The operating system software will maintain both RAIDs.

Once you make a RAID, the software treats it just like a single disk, and you can carve up the RAID into different partitions. So, when you install, create a small RAID-1 out of 100 Mb partitions (one from each disk), and then on that RAID-1 device create a single partition, formatted ext3, and assign it the mount point **/boot**.

Out of the rest of the space on the three disks, make a RAID-5. Once you have created your RAID-5 device, make a 1 GB partition to use as swap, which is a virtual memory space that the operating system uses. From the rest make an ext3 partition to use as your root file system, with the mount point **/** (called "root"). After you have created these partitions, the installer will automatically put the boot images into the /boot partition, and the rest of the software into /. It will also activate and use the swap partition too.

You get the Alternate Install CD from the [Ubuntu Download]("http://www.ubuntu.com/GetUbuntu/download") page, just check the box below the Start Download button.

---

### Post by rgotten on 2008-04-07
OK, I am planning to install the ubuntu server edition; is the alternate install cd only to do the raid or is for installing the whole thing. (in that case, is it for the server edition?) Were can i get good and simple instruction on how to do this..Sorry, linux/ubuntu is completely new for me, but guidence and help are alwyas well appreicated...Thanks for understanding and providing me with this help

rgotten

---

### Post by dstew on 2008-04-08
The Alternate Install CD will install the server or full (desktop) system, whichever you want. [Here]("https://help.ubuntu.com/community/Installation/I386") is a guide for installing from the Alternate Install CD. If you want to create and install to RAIDs, [this page]("http://users.piuha.net/martti/comp/ubuntu/en/raid.html") is excellent, has screenshots. He only creates a RAID-1, but the same steps are used to create a RAID-5. During the installation, you can go back to previous steps and try again if you are not sure. I pretty much figured it out on my own, by going back and forth until I had a good feel for what I was doing.

After you create your RAIDs, create partitions within the RAIDs, assign them mount points as I discussed above, and format them with the appropriate formats. Then,  the installer will install the base (server) system. After that, you get a screen for installing more software. If you just want the absolute base system, leave blank (or uncheck) the boxes, and the installation will finish. You can always install software later using apt-get.

---

### Post by rgotten on 2008-04-08
> **dstew said:**
> The Alternate Install CD will install the server or full (desktop) system, whichever you want. .

When i try to donwload there is the desktop and the server selection, when i select to download with or without checking the alternate cd, and I select the server edition it shows the file as " Ubuntu 7.10 server 64amd.iso" (the same thing checking or not cheking the alternate cd box), when i select the desktop edition, and check the alternate cd, it says " Ubuntu 7.10 alternate 64amd.iso" compare with  Ubuntu 7.10 desktop 64amd.iso" when i uncheck the box for alternate CD?? That is why i was asking if that will install the server edition, or i have to instal the full desktop edition  and then  add the server (i heard is heavier and uses more resources or i can just select to instal the server edition with LAMP from  the alternate cd),  Also for the intel duo core i am selecting the optio of 64bit AMD and Intel computers (is this correct?)

---

### Post by dstew on 2008-04-08
> the same thing checking or not cheking the alternate cd boxI think the Server .iso is the same as the Alternate Install .iso (text-based installation interface) except the Alternate Install allows you the option of installing the Ubuntu Desktop. I am not sure if the Server .iso will let you configure a RAID, but it probably will. My experience is with the Alternate Install .iso that has on it the Ubuntu Desktop software.> i can just select to instal the server edition with LAMP from the alternate cdYes, you can do this. I am pretty sure the Alternate Install will offer to let you install LAMP at the end, and also gives you the option of not installing the Ubuntu desktop.

I think the 64-bit AMD .iso is the one you want for an Intel Core Duo processor, but sometimes certain hardware drivers are balky in the 64-bit system. You might find you need to install the 32-bit system to get certain devices to work properly. But, that is usually for graphic display adapters and wireless cards, and you probably won't be using these in your server anyway, so go ahead and install the 64-bit system.

---

### Post by rgotten on 2008-04-19
Thanks for all your replies and isntructions. I have follow them and was able to do the configuration you show me. This is the new questions I have:

1) When i remove one hard drive trying to simulate a failure, it does not boot. (i install the boot information to each one of the hard drives
2) The swap, i have read on this forum to make it RAID 0, (will this work if there is a failure) or as small swap os each hard drive (not as raid) I try number 1 and number 2, and you mention as part of the raid 5 (i was not able to do this (when i try to repartition inside the raid 5 to do this it only let me do one partition--maybe i am doing something wrong)
3)When it boots up with the 3 hard drive and boots normally, i see the ligth of the hard drives on at all times...is this normal???

4) can you please in simple words explain to me what is the difference between /boot and / and /home.....sombody even mention to me that i have to made a raid 1 with two partitiosn one of 100 mb of /boot, one of 5 gb of / and then the raid 5 /home

Also i found this link: [http://ubuntuforums.org/showthread.php?t=699075](http://ubuntuforums.org/showthread.php?t=699075) where he talks about /var and /tmp in your opinion and on what i whant to achiev do i need to do this?? He also does some other stuff wit the os..is this what i did, or si something i should do??/

Thanks one more time

rgotten

---

### Post by rgotten on 2008-04-29
I am in the process of installing my server and have being trying for the last few weeks diferet options on isntalling my raid and be able to boot. I am installing the boot on Raid 1 128mb, Swap on Raid 1 (2gb), the root on raid 5 (10 gb) and the rest for home on Raid 5 ( aprox. 960 gb).
For doing this i am using 3 hard drive 500 ngb each. Before the 8.04 relaese i had to install the boot instruction on each one of the hard drive (device (hd1) /dev/sda
root (hd1,0)
setup (hd1)
device (hd1) /dev/sdb
root (hd1,0)
setup (hd1)
device (hd1) /dev/sdc
root (hd1,0)
setup (hd1)
so if one fails the raid can be started from the other hard drive. With version 8.04, when i disconect either of the hard drive it appears to boot and i get a message that says: start the raid in degrade (or somethng similar), with the command mdadm -R /dev/mdx ( in version 7.10, i have to install the boot insruction in each one of the hard drive). Since i am getting this message, does this mean that the newer version has the bug fixed in regards to the instruction on how to boot in each one of the hard drive??

How can i check each hard drive to be sure they have this instruction and that i have installed grub also on the second disk's (/dev/sdb) master boot record (MBR), as well as the third. ??

rgotten

---


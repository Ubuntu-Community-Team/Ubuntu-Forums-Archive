---
title: "Another Installation Problem (No Root"
date: 2007-03-09
forum: Apple Intel Users
---

### Post by amb1s1 on 2007-03-09
I'm trying to do the triple boot. I already have XP through BootCamp. What I did I created a 3rd partition and I went and boot with the ubunta live cd. I have three Partition one 45GB for my MAC OS another 10G for XP and 10G ready for linux. Now I'm on Prepare Disk Space. I have three choices:
1 Erase entire disk: SCSI1 (0,10) (SDA) - 80 GB ATA Toshiba MK8034GS
2 Use the largest continuous free space
3 Nabually edit partition table

I know for sure that is not going to be number one because I don't want to erase the entire drive. My next choise is number 2, I choose that one, but I get "No root file system is defined.
                                                                             Please correct this from partition menu.
My last option is 3, but I'm not sure how to do that. Can anybody help pass this problem. Thanks

---

### Post by mac.ryan on 2007-03-09
> **amb1s1 said:**
> My last option is 3, but I'm not sure how to do that. Can anybody help pass this problem. Thanks

I am not a mac user, but if the question is about size and type of partitions, then the most common way to partition for ubuntu is:
[LIST=1]
[*]10Gb primary EXT3 partition (here you will install ubuntu)
[*]Your RAM size X times (1<X<2) SWAP partition
[*]XXGb EXT3 partition (you will mount this partition as /home)[/LIST]If XOS already have a swap partition (I read it is posix system) you should be able to use for ubuntu the same swap partition without problems.

The advantage in keeping your data (/home) separate from your system installation is that it is safer and allows easier upgrades of ubuntu, but it is not compulsory, a single EXT3 partition + swap will do the trick as well.

---

### Post by amb1s1 on 2007-03-10
Now I'm getting the following message:
" Executing 'grub -install (hd0) failed. This is a fatal error. Any help

---

### Post by mac.ryan on 2007-03-10
> **amb1s1 said:**
> Now I'm getting the following message:
" Executing 'grub -install (hd0) failed. This is a fatal error. Any help

I have the impression this means that when installing GRUB (the bootstrap loader, i.e. the programme that let you choose what OS you want to use) on your main HD, there is an exception.

As stated above, I am not a mac user, but - if you already have a mac boot loader that lets you choose between OSX and Windows when you power on, then it would probably enough to add the line explaining to it where ubuntu is, in order to have the three systems up and running. In other words: you might not need grub at all. From google I understood the boot loader in OSX is called "yaboot", but - as stated before - I don't own a mac and mine is therefore just second hand information... :)

---

### Post by amb1s1 on 2007-03-10
How can I stop ubuntu to stop installing Grub. Tha was my thought firt, but I didn't see an option to stop grub.

---

### Post by mac.ryan on 2007-03-10
> **amb1s1 said:**
> How can I stop ubuntu to stop installing Grub. Tha was my thought firt, but I didn't see an option to stop grub.

If my memory doesn't betray me (I have not live CD at hand) you should press F6 when starting the installation (so you enter in "expert mode") from there,  that way, at some point of the installation, the option to install / not install GRUB should show up...

I would be very happy - anyhow - if any mac user **who actually did** the installation would join in the discussion! :)

(...I might have to do it myself in a few weeks time...) :(

---

### Post by amb1s1 on 2007-03-10
When I click F6, an thing pop up where there is something already write on. I click enter and I when back to the same live cd. This is very frustrating, I think this is one of the reason not a lot of people like Linux. I'm doing this for learning experience. If I would be a regular user, no way way would go through this

---

### Post by mac.ryan on 2007-03-10
> **amb1s1 said:**
> When I click F6, an thing pop up where there is something already write on. I click enter and I when back to the same live cd. 

Yes, I think the option about GRUB will show up after you install... (I did it long time ago, I can't really remember exactly when). So: press F6 --> Install --> Get the option about GRUB.

> This is very frustrating, I think this is one of the reason not a lot of people like Linux. I'm doing this for learning experience. If I would be a regular user, no way way would go through thisAlthough I simpatise with your frustration (this is why after all people help out people on the forum), I am still convinced is a matter of points of view: if ubuntu was your primary OS, then you would be struggling with the installation of OSX as secondary OS and you would probably comment something "I can't understand why I should pay such a crappy system"... I know OSX very superficially, but with M$ Window$, installing a dual boot option... is neither a possibility! As ever, the tricky point is to keep in mind that what is familiar looks like easy but could also not be such, and vice versa...

Keep on with the struggle, I can assure you that once you overcome the  initial difficulties that are there any time you face something new, working with linux is VERY rewarding! :)

Best luck!

---

### Post by amb1s1 on 2007-03-10
I'm going to keep trying and trying until I get it done. I work as a helpdesk for Great Atlantic and Pacific and I hear that in the future all the store are going to move from Unix (AIX)$$$ to Linux and I would like to know little more linux because at the end I want to be a Unix Admin.

---

### Post by Gen2ly on 2007-03-11
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by Chrisj303 on 2007-03-11
Read steps 6 + 7 of this guide : [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

I got the triple boot - OSX/UBUNTU/XP on my macbook last week using GRUB. It works fine, except for one FATAL flaw - The keyboard is only responsive to the GRUB bootloader about 20% of the time. As a result if you want to boot into a non-default OS in Grub, you have to keep re-booting until the keyboard works as you can't scroll down the list!
Using a USB keyboard makes no difference either. I have searched and searched the internet for a soloution to no avail.
I'm telling you this, as you MAY want to stop and try again using LILO. This is what i'm in the process of doing now. But it takes a little more work, and to a total Linux beginner like myself easy to follow help is hard to come by.

---

### Post by amb1s1 on 2007-03-11
> **Dirk.R.Gently said:**
> [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Thanks, It is installed. Now I'm stock on step 10 getting my wireless to work:

sudo apt-get install ndiswrapper-utils-1.8
sudo mount /dev/sda4 /mnt - when I do this I get: /
dev/sda4 looks like swapspace - not mounted
mount: you must specify the filesystem type


sudo ndiswrapper -i "/mnt/Program Files/Macintosh Drivers for Windows XP 1.1.2/net5416/net5416.inf" ----- IN This part do I need to have the CD that burned with all of the Mac-windows drive
sudo modprobe ndiswrapper
sudo echo >> /etc/modules "ndiswrapper"
sudo umount /mnt

---

### Post by Chrisj303 on 2007-03-11
^Is your GRUB loader working properly - or are you having troubles selecting your OS?
I'd be interested to know wether i was just unlucky, or if thats the norm...

I've got the triple boot with LILO now, and it's working perfectly!

---

### Post by ouilsen on 2007-03-11
I posted [here]("http://www.ubuntuforums.org/showthread.php?t=378259") on how I did the partitioning on my macbook c2d. Hope this helps. That was when I installed feisty herd 5.

Edit: Don't delete /dev/sda3. That might be your Windows parition. It should be /dev/sda4 or something on your disk.

Edit 2: O well... sorry didn't see it was solved. Now the wireless. At least on herd 5 I had to download the newest ndiswrapper version, compile it and use the lenovo thinkpad drivers, but I suppose that's not your system.

---


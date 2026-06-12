---
title: "I can't access all of my HD's in Ubuntu"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by maximo on 2006-09-19
I have a 250 gig partitioned (slpit in half pretty much), a 80 gig, and a 40 gig (ubuntu is installed on this one). Ubuntu only recognizes part of my 250 gig and I can't access any of my HD's besides the one that Ubuntu is installed on. I wanted to add music to the amaroK player, but it won't let me. I simply tried to view the folders in the HD under Places->computer and it gives me an error which says "unable to mount the selected device." The details say, "error: device /dev/sda1 is not removable" and "error: could not execute pmount." All I want to do is access the files.

---

### Post by yellowband on 2006-09-19
what is the output when you give the command:

fdisk -l

in the terminal?

---

### Post by maximo on 2006-09-19
I'm still new to this whole terminal thing. I've been just trying to double click on the drives. Do I need to type something in the terminal instead?

---

### Post by pesach on 2006-09-19
Yes. Open a terminal and write
```
 fdisk -l 
```
l as in lowercase L
the terminal can be found under "accesories"

---

### Post by maximo on 2006-09-19
> **pesach said:**
> Yes. Open a terminal and write
```
 fdisk -l 
```
l as in lowercase L
the terminal can be found under "accesories"

I'm sure that I'm doing something wrong. But, here's what it says. After I type in fdisk and hit enter it tells me this: 

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices

And, no matter what I type in, it says unable to open. For example, I copied fdisk /dev/hda (and the other three) and then pasted it and hit enter and it says:

Unable to open /dev/sdc
steven@steven-desktop:~$ fdisk /dev/hda

Unable to open /dev/hda
steven@steven-desktop:~$ fdisk /dev/rd/c0d0

Unable to open /dev/rd/c0d0
steven@steven-desktop:~$ fdisk /dev/hda

---

### Post by chrdior on 2006-09-19
[-x

---

### Post by MetalMusicAddict on 2006-09-19
What filesystems are you using on the other partitions/HDs? Do you dual-boot?

---

### Post by maximo on 2006-09-19
> **MetalMusicAddict said:**
> What filesystems are you using on the other partitions/HDs? Do you dual-boot?

They're probably ntfs. I know that my 250 gig is ntfs. I can't remember if my 80 has ever been formated. I have windows xp prof. on the 250. It's pretty much partitioned into two equal drives. Ubuntu is installed on my 40 gig.

---

### Post by crokett on 2006-09-19
maximo,

try:

```
sudo fdisk -l
```

in your terminal window

---

### Post by mongooseman1128 on 2006-09-19
make sure the drives aren't failing with a HDD utility like DFT (drive fitness test) and also is the 80 gig an unformatted HDD? because if it is you should format then be good

---

### Post by maximo on 2006-09-19
> **crokett said:**
> maximo,

try:

```
sudo fdisk -l
```

in your terminal window

I've done this. It pops this up: 
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

I then try to copy and paste each of the lines to see if I can get any to work and each give me an error.

---

### Post by rockstar on 2006-09-19
Now what?  It doesn't look like the question got answered.  I followed all the steps and I still have the same problem as Maximo. I partitioned my hard drive and formatted the extra space as FAT32 so that I could read and write it in Ubuntu and Windows but I don't know why the hard drive wont mount

---

### Post by MetalMusicAddict on 2006-09-19
Heres what one of my FSTAB lines looks like for NTFS drives/partitions.

```
[COLOR="Red"]/dev/hdb1[/COLOR]       [COLOR="Blue"]/media/RipTemp[/COLOR]     **ntfs    nls=utf8,umask=0222 0       0**
```
The pathes are gonna be specific to you but the stuff in **BLACK** should give you read access.

The path in [COLOR="Red"]RED[/COLOR] points to you device. The path in [COLOR="Blue"]BLUE[/COLOR] is where you wanna see it.

---

### Post by maximo on 2006-09-19
> **MetalMusicAddict said:**
> Heres what one of my FSTAB lines looks like for NTFS drives/partitions.

```
[COLOR="Red"]/dev/hdb1[/COLOR]       [COLOR="Blue"]/media/RipTemp[/COLOR]     **ntfs    nls=utf8,umask=0222 0       0**
```
The pathes are gonna be specific to you but the stuff in **BLACK** should give you read access.

The path in [COLOR="Red"]RED[/COLOR] points to you device. The path in [COLOR="Blue"]BLUE[/COLOR] is where you wanna see it.

This is driving me crazy. lol. I've tried all this and I'll I get is access denied. I'm been searching google and have noticed others with problem. I found a guy who said he has a solution, but I'm not sure how to execute what he's saying. I'll quote him (it's acutally on these forums somewhere): 

"July 18th, 2006, 05:33 PM
I have found the answer !!

(I'm new to this though so bare with me if anything is wrong.)

The problem is when clicking on 'Places' then 'Computer' in ubuntu 6.06. The windows partitions which are automatically detected are not accessible, and you receive the following error:-

Unable to mount the selected volume
error: device /dev/hda2 is not removable
error: could not execute pmount

This is because pmount is being used by the system instead of mount. pmount is used because it can be executed by normal users. However pmount is designed for removable media and only if the user has the permission to mount removable devices.

I looked in the help for pmount, by typing 'man pmount' and found that non-removable devices can also be mounted if they are listed in the pmount.allow file.

So edit the file and add the device to the end of the file. In my case I typed 'sudo vi /etc/pmount.allow'

Then navigated to the end of the file. Pressed 'a' for append. Then typed the device. For me that was:-

/dev/sdb1

I then saved the file by typing

Esc : wq Enter

I was then able to mount the partition using the browser.

Hope that helps, its been very interesting learning this so far!

Daniel Ellis."

---

### Post by confused57 on 2006-09-19
Here's a howto for mounting Windows:

[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

Edit:  See you've already figured it out using pmount file...good for you.

---

### Post by MetalMusicAddict on 2006-09-19
You did create the folder you wanted to mount the drive to? You did reboot after you changed the FSTAB right maximo? Its weird you have a problem. That works just fine for any NTFS drive/partition I have.

---

### Post by maximo on 2006-09-19
> **MetalMusicAddict said:**
> You did create the folder you wanted to mount the drive to? You did reboot after you changed the FSTAB right maximo? Its weird you have a problem. That works just fine for any NTFS drive/partition I have.

Ok, some good news. I got one of the drives working so far. Yeah! lol. But, Ubuntu just doesn't seem to recognize my both parts of my 250 gig hd. It only sees the partitioned space where windows is actually installed. I have all my music and pictures installed on the other half. How do I find it?

---

### Post by maximo on 2006-09-19
/dev/sda2      /windows ntfs nls=utf8,umask=0222 0 0

I copied this line for both partitioned spaces. I gues I'm suppose to change the location on one or something. It's actually showing the drive that I want in windows now. But, what if I want to see both. What should I change? Should I just create a new folder and put something like /windows/drive2 or something?

---

### Post by MetalMusicAddict on 2006-09-20
> **maximo said:**
> /dev/sda2      /windows ntfs nls=utf8,umask=0222 0 0

I copied this line for both partitioned spaces. I gues I'm suppose to change the location on one or something. It's actually showing the drive that I want in windows now. But, what if I want to see both. What should I change? Should I just create a new folder and put something like /windows/drive2 or something?

Your getting the path where you need to mount the device wrong. Things should be mounted in you "/media" folder. ie: /media/windows or /media/storage. Either way "/media" should be there 1st.

To create a folder there do this from a terminal: **sudo mkdir /media/windows**. It also works to do multiple folders at once like: **sudo mkdir /media/windows /media/storage**. Just seperate the dirs by a space. Change your FSTAB to reflect the path.

Have you read the links people posted? They are telling you about the same thing.

---

### Post by apkolev on 2006-09-20
Hi!

I had the same problem. After creating directories that you are going to use for mount points you can try this: ***sudo disks-admin***. The interface allows to choose a drive and partition that you would like to mount, the directory (/media/something) and just click "Enable".

Cheers!

---

### Post by maximo on 2006-09-20
> **MetalMusicAddict said:**
> Your getting the path where you need to mount the device wrong. Things should be mounted in you "/media" folder. ie: /media/windows or /media/storage. Either way "/media" should be there 1st.

To create a folder there do this from a terminal: **sudo mkdir /media/windows**. It also works to do multiple folders at once like: **sudo mkdir /media/windows /media/storage**. Just seperate the dirs by a space. Change your FSTAB to reflect the path.

Have you read the links people posted? They are telling you about the same thing.

I'm starting to understand all this a little better (a little being the key here). I've got my drives showing by following the directions from each of you. They appear as New Volume (/media/storage) and Windows (/media/windows). I have a thrid drive that I want to see. Should I create a new folder? I tried to create /media/storage2, but it won't let me. I guess it has to be a certain name. Or, should I just direct (or mount whatever it is called) the drive to one of the existing loctions such as /media/storage. I'm not even sure that will work. 

Thanks for being patient. I'm trying to learn.

---

### Post by MetalMusicAddict on 2006-09-20
Really my post #13 says it all. The 1st path is to the actual device. The 2nd is where you want it to go. (should always start with "/media") and then after that are the options for the drive. Thoes explained is a whole nother thread. :)

I will say though there is this whole thing where Im getting drives mounted twice sometimes. HAL is mounting them also I think.

In windows what are the drives you want to mount called? PM me if you have AIM or MSN messenger.

---


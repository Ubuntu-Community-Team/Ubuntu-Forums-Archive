---
title: "Not creating a bootable usb"
date: 2010-04-24
forum: Apple Hardware Users
---

### Post by 64bprophet on 2010-04-24
Hey All,
I've been searching all over the place for a solution to this and I honestly am coming up empty.

I am working on a Macbook pro 13" model and I am trying to get a bootable version of Ubuntu to work from a USB drive. (16gb Crucial) I've been following the instructions here: [https://help.ubuntu.com/community/Installation/FromUSBStick#From](https://help.ubuntu.com/community/Installation/FromUSBStick#From) Mac

And while they copy everything to the usb drive it doesn't make the drive bootable. (Either for my Mac or on my wife's Dell) I've tried this with the normal 32bit bootable "live" version 9.10 as well as the rc of 10.04. I've also tried it with the netbook version of 9.10 as well. They all copy just fine, but the boot sector seems to missing. What am I missing?!

(I also tried burning a CD of the same image (10.04) to see if it would make the CD bootable, but I had the same issue. Content, but no boot sector.)

I figure it has to be me, as 3 images can't be wrong here. (I am following those instructions at the link above to the letter. I've checked them 4 or 5 times now. 

Any tips or suggestions would be greatly appreciated. (I'm running OSX 10.6.3 fyi)

---

### Post by garvinrick4 on 2010-04-24
> **64bprophet said:**
> Hey All,
I've been searching all over the place for a solution to this and I honestly am coming up empty.

I am working on a Macbook pro 13" model and I am trying to get a bootable version of Ubuntu to work from a USB drive. (16gb Crucial) I've been following the instructions here: [https://help.ubuntu.com/community/Installation/FromUSBStick#From](https://help.ubuntu.com/community/Installation/FromUSBStick#From) Mac

And while they copy everything to the usb drive it doesn't make the drive bootable. (Either for my Mac or on my wife's Dell) I've tried this with the normal 32bit bootable "live" version 9.10 as well as the rc of 10.04. I've also tried it with the netbook version of 9.10 as well. They all copy just fine, but the boot sector seems to missing. What am I missing?!

(I also tried burning a CD of the same image (10.04) to see if it would make the CD bootable, but I had the same issue. Content, but no boot sector.)

I figure it has to be me, as 3 images can't be wrong here. (I am following those instructions at the link above to the letter. I've checked them 4 or 5 times now. 

Any tips or suggestions would be greatly appreciated. (I'm running OSX 10.6.3 fyi) I will tell you I have used a lot of different types of USB flash drives to
boot from and some just do not want to boot, that is all there is to that. Others will work
everytime.  CENTON is the only one to work as a bootable drive from 16 gig down to the 4 gig. Some of the other brands will work on unetbooten but not Start-updisk-creator. Some will not work at all but as I say CENTON has worked in every package and even when I installed with a /boot a /  and a swap. in ext4 format. Who knows why.

---

### Post by wilee-nilee on 2010-04-24
With that size of a thumb I would if it works for you do a full install on it. You can set it up with a Ubuntu plenty of space and also have a fat32 partition for macs or ms to read.

If you do a full install be very careful grub will probably default to the HD on the computer your installing with so hit that advanced button in the last gui of the install and point grub at the device with no partition #.

---

### Post by 64bprophet on 2010-04-24
> **wilee-nilee said:**
> With that size of a thumb I would if it works for you do a full install on it. You can set it up with a Ubuntu plenty of space and also have a fat32 partition for macs or ms to read.

If you do a full install be very careful grub will probably default to the HD on the computer your installing with so hit that advanced button in the last gui of the install and point grub at the device with no partition #.

So then are you suggesting I use a Live CD, and then install the full thing to the usb drive?

---

### Post by 64bprophet on 2010-04-24
> **garvinrick4 said:**
> I will tell you I have used a lot of different types of USB flash drives to
boot from and some just do not want to boot, that is all there is to that. Others will work
everytime.  CENTON is the only one to work as a bootable drive from 16 gig down to the 4 gig. Some of the other brands will work on unetbooten but not Start-updisk-creator. Some will not work at all but as I say CENTON has worked in every package and even when I installed with a /boot a /  and a swap. in ext4 format. Who knows why.

Ok, I get that some USB drives refuse to boot. I'll try a few, smaller, ones I have lying around and see what happens.

However this doesn't explain why when I use the exact same image file the CD I burned isn't bootable. Both were created on this Mac. Both won't boot. (From at least 2 images) I would understand if the USB drive didn't boot but the CD did. But that isn't the case. Which gives me some hope that the USB still might be bootable.

---

### Post by 64bprophet on 2010-04-24
Not to bog down this thread with comments from me, but I have some more information. I used my wife's laptop (Dell, Win7) to download the 10.04 ISO, I then burned a live CD (which was bootable), booted off of it, and ran an install on my 16gb USB drive. The installation went very well (didn't touch her win7 install). After the install I checked and confirmed her machine booted safely into windows and then rebooted her machine again and put the USB drive in. I was able to boot off of it without any problems and had a fully working Ubuntu install. 

Then I put it into my macbook pro, rebooted the system and told it to check for alternate methods of booting (alt/option), all it showed me was the HD in the laptop. Even when I booted into OSX it didn't recognize the USB drive as bootable in the startup disk area. So, what am I missing here. Works fine on a windows machine, but no response from a mac. Ideas? Thoughts?

---

### Post by buntuLo on 2010-04-24
did you try installing rEFIt on the macbook drive? you can even just use it from cd, without installing it. it is a boot selector and - in my case- it does see bootloader executables (grub, grub2, ...) also on external drives.
by the way, i also had troubles with many usb drives, but kingston worked always fine for me.

---

### Post by xxander on 2010-04-24
Hello! I have solutions for you because I just recently installed Ubuntu on my MacBook.  It took me forever to figure out, but I'll be glad to help.  

First off, Macs cannot boot an OS from a USB drive without the help of a third party application called rEFIt.  The first time I installed this, it bricked my computer (unable to start), and spent a night at the Apple Store getting repaired.  

I recommend using Boot Camp Assistant (application on MacBook) to partition your hard drive.  Then, burn the ISO of Ubuntu to a CD, and boot your computer from the CD (hold down 'c' or 'option').  After this, select your language and all of that, and once you get to the partition step, choose the second option (I think) (it will be the one that lets you drag to scale) and make the Ubuntu cover the Boot Camp section.  You will now be good, and if you want to boot into Ubuntu when you turn on your computer, hold down the option key.  

I hoped this helped!  I spent over a week researching and trying this, and there are MANY ways to do it.  I find this one the most stable.  

ALSO, once you start using Ubuntu, there are many things you must fix to make everything run well. (like track pad and wireless)  Hopefully, you won't have this problem too!  I you do, just PM me.  I might make a guide in the future for MacBook and MacBook Pro users.

Good luck Ubuntu'ing'!

---

### Post by art4med on 2010-04-25
[Neds Moar Salt]("http://ubuntuforums.org/member.php?u=1040535")'s tut on this is in [http://ubuntuforums.org/showthread.php?t=1443387](http://ubuntuforums.org/showthread.php?t=1443387) 
**Please choose a thread for updates......**
I'll be looking on the thread of the tut (above link).
Thanks, xxander, this may solve a prob for me....
or are you one and the same?

---

### Post by 64bprophet on 2010-04-25
Well, I don't want to install Ubuntu on my macbook pro, I just want it to run off of my USB drive, and I'm not going to install something that might brick my MBP just to make that happen. 

I think the instructions at the link I listed above seem to be inaccurate then. If what you all are saying, that you need a 3rd party bootloader just to get OSX to see your Ubuntu installer then the instructions on how to get a bootable USB drive with Ubuntu on it for the Mac are incorrect and need to be fixed/ removed.

I'm new here so I am not really sure how to suggest, officially, that I think the OSX instructions are in need of retooling.

---

### Post by buntuLo on 2010-04-25
> **64bprophet said:**
> Well, I don't want to install Ubuntu on my macbook pro, I just want it to run off of my USB drive, and I'm not going to install something that might brick my MBP just to make that happen.
did you actually read my post?
> **buntuLo said:**
> you can even just use it from cd, without installing it. it is a boot selector and - in my case- it does see bootloader executables (grub, grub2, ...) also on external drives.
rEFIt is not a bootloader, only a selector, which lets you choose between different bootloaders. every OS needs a bootloader (grub, grub2, apple bootloader, ...) to boot. while the selector (rEFIt) is not strictly necessary, it helps finding the bootloader, especially on external drives.
moreover you do NOT need to install rEFIt, but you can just run it off the cd: burn it, boot the rEFIt cd (using ALT+C) with the usb-stick plugged in, and rEFIt should recognise the bootloader (grub for ubuntu) present on your stick.
just give it a try, then you come back with your comments about the porcedure and other documentation pages. good luck!

---

### Post by jbiggs12 on 2010-04-25
From my experience, getting Macs to boot from USB has been a really ornery task. If you're absolutely desperate to get Ubuntu running on your Mac, and don't want to risk wiping your hard drive when you install (installing Ubuntu dual-boot on a Mac isn't actually that difficult, Boot Camp makse the partition and you just tell Ubuntu to install to it), I'd recommend trying out VirtualBox instead of tearing your hair out trying to get the flash drive to work.

Some Macs won't even boot off of a flash drive. My MBP won't.

---


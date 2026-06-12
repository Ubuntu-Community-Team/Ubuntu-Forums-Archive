---
title: "Is booting from a thumb drive possible on an Apple?"
date: 2011-02-22
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2011-02-22
I find Live CDs quite useful, whether it be for fixing stuff or restoring stuff or repartitioning stuff. Ubuntu Live CDs can just do a lot of stuff:p. However, I've never been crazy about the speed. DVD drives are just limited.

So on several occasions, I've tried to (according to the Ubuntu website walkthrough) create a "Live CD" on a 2 GB thumb drive I had lying around, with no success. I thought it was just my flash drive, so I bought a new one (4GB, different company) and again, negative with the success.

I've since tried installing Ubuntu on both drives (Netbook edition on the 4GB, Xubuntu on the 2GB), and it still didn't work.

This certainly isn't any sort of priority, as I'm looking at creating a "recovery drive," with a variety of small OSes to help fix/partition/create/destroy/hack/slash/jump/backspace things. However, a portable (as in flash drive) portable (as in usable on multiple systems) Ubuntu would be quite handy. And a flash drive is awfully small.

Is it possible to make a flash drive into a Live CD which will boot using rEFIt? Or, if not, can I install Ubuntu onto a flash drive and make it bootable? If "no" on either one, then why is this the case?

Thanks!

---

### Post by Hatsune Miku on 2011-02-23
> **teamjh14 said:**
> I find Live CDs quite useful, whether it be for fixing stuff or restoring stuff or repartitioning stuff. Ubuntu Live CDs can just do a lot of stuff:p. However, I've never been crazy about the speed. DVD drives are just limited.

So on several occasions, I've tried to (according to the Ubuntu website walkthrough) create a "Live CD" on a 2 GB thumb drive I had lying around, with no success. I thought it was just my flash drive, so I bought a new one (4GB, different company) and again, negative with the success.

I've since tried installing Ubuntu on both drives (Netbook edition on the 4GB, Xubuntu on the 2GB), and it still didn't work.

This certainly isn't any sort of priority, as I'm looking at creating a "recovery drive," with a variety of small OSes to help fix/partition/create/destroy/hack/slash/jump/backspace things. However, a portable (as in flash drive) portable (as in usable on multiple systems) Ubuntu would be quite handy. And a flash drive is awfully small.

Is it possible to make a flash drive into a Live CD which will boot using rEFIt? Or, if not, can I install Ubuntu onto a flash drive and make it bootable? If "no" on either one, then why is this the case?

Thanks!

I've got it to work Once or Twice, its a bit finicky. Use rEFIt to have the EFI framework see the Linux kernel and be able to start the boot process. Gl!

---

### Post by Ben Page on 2011-02-23
If your Apple PC supports booting from USB, then using portable Ubuntu is possible. You have to*make a bootable USB installation, I recommend LiLi to do this [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) (sadly works on Windows only, but it's dead simple) or you can follow the instructions on Ubuntu.com site 

```
   1. Download the desired file
   2. Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
   3. Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
   4. Note: OS X tends to put the .dmg ending on the output file automatically.
   5. Run diskutil list to get the current list of devices
   6. Insert your flash media
   7. Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
   8. Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)
   9. Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
  10.
          * Using /dev/rdisk instead of /dev/disk may be faster.
          * If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
          * If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
  11. Run diskutil eject/dev/diskN and remove your flash media when the command completes
  12. Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick

```

---

### Post by Hatsune Miku on 2011-02-23
> **Ben Page said:**
> If your Apple PC supports booting from USB, then using portable Ubuntu is possible. You have to*make a bootable USB installation, I recommend LiLi to do this [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) (sadly works on Windows only, but it's dead simple) or you can follow the instructions on Ubuntu.com site 

```
   1. Download the desired file
   2. Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
   3. Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
   4. Note: OS X tends to put the .dmg ending on the output file automatically.
   5. Run diskutil list to get the current list of devices
   6. Insert your flash media
   7. Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
   8. Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)
   9. Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
  10.
          * Using /dev/rdisk instead of /dev/disk may be faster.
          * If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
          * If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
  11. Run diskutil eject/dev/diskN and remove your flash media when the command completes
  12. Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick

```

Ive' tried this before, it never worked :P! Anyway just use unetbootin, that was i did to get it working.

---

### Post by Tu1J4kXk8NUhMz on 2011-02-23
> **Hatsune Miku said:**
> I've got it to work Once or Twice, its a bit finicky. Use rEFIt to have the EFI framework see the Linux kernel and be able to start the boot process. Gl!

I am using rEFIt, for sure. It has yet to pick it up. I've never had any issue running Ubuntu or even a OS X bootable drive through rEFIt, but for whatever reason it gives me grief when using a thumb drive.

> **Hatsune Miku said:**
> Ive' tried this before, it never worked :P! Anyway just use unetbootin, that was i did to get it working.

I've tried unetbootin with no success. It's been a while since I've used this software, so perhaps I did it wrong and got annoyed and said "#!@$ it!" Now that I think about it, I believe I was using some sort of obscure Ubuntu derivation...that might've been the issue. I'll try again.

> **Ben Page said:**
> If your Apple PC supports booting from USB, then using portable Ubuntu is possible. You have to*make a bootable USB installation, I recommend LiLi to do this [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) (sadly works on Windows only, but it's dead simple) or you can follow the instructions on Ubuntu.com site 


Never even heard of LiLi...if I don't have any luck with unetbootin, I'll give this a shot.

The instructions the Ubuntu website gives I believe to be faulty, at least on a Mac. The process they provide merely translates the ISO onto the thumb drive, making it a "CD" (it changes the drive's format to ISO9660), to which Mac OS X (I suspect) says, "Wait a minute....that's not a CD!"

Anyhow, thanks for the input, guys! Hopefully one of these will stick...I'll report back when I'm done.

---

### Post by Chris Grk-O-Matic on 2011-02-23
[http://lifehacker.com/5739259/how-to-create-a-portable-hackintosh-on-a-usb-thumb-drive](http://lifehacker.com/5739259/how-to-create-a-portable-hackintosh-on-a-usb-thumb-drive)

---

### Post by Tu1J4kXk8NUhMz on 2011-02-23
> **Chris Grk-O-Matic said:**
> [http://lifehacker.com/5739259/how-to-create-a-portable-hackintosh-on-a-usb-thumb-drive](http://lifehacker.com/5739259/how-to-create-a-portable-hackintosh-on-a-usb-thumb-drive)

This is not helpful to my problem.

> **teamjh14 said:**
> I've tried unetbootin with no success. It's been a while since I've used this software, so perhaps I did it wrong and got annoyed and said "#!@$ it!" Now that I think about it, I believe I was using some sort of obscure Ubuntu derivation...that might've been the issue. I'll try again.

Still no luck...

> Never even heard of LiLi...if I don't have any luck with unetbootin, I'll give this a shot.

No go.

I have tried LiLi, UNetBootin, and (Ubuntu's suggestion) Universal USB Installer. I've had more success than previous tries using Mac OS X: the USB shows up as a bootable device. I'm able to select the drive in rEFIt, but instead of loading up Ubuntu, it goes to a black screen momentarily, then loads up Windows 7.

I feel like I'm getting closer, but no cigar. Suggestions?

---

### Post by pindar on 2011-02-23
> **teamjh14 said:**
> 
Is it possible to make a flash drive into a Live CD which will boot using rEFIt? Or, if not, can I install Ubuntu onto a flash drive and make it bootable? If "no" on either one, then why is this the case?
To come back to your initial question: yes and no. Unfortunately, for apple hardware, there is no clear answer. It depends on your hardware, it depends on the version of ubuntu (or other linux distributions) you want to use, and it may even depend on the usb stick you use. That being said: I have been able to boot an iso of ubuntu 10.10 (maverick) from a usb stick both on my macbook (1,1) and on my mac mini (first time I get it to boot off of a usb stick at all). [This thread]("http://ubuntuforums.org/showthread.php?t=1504038") has some useful info. But be warned that the process is somewhat convoluted and success isn't guaranteed.

Good luck!

---

### Post by Tu1J4kXk8NUhMz on 2011-02-23
> **pindar said:**
> To come back to your initial question: yes and no. Unfortunately, for apple hardware, there is no clear answer. It depends on your hardware, it depends on the version of ubuntu (or other linux distributions) you want to use, and it may even depend on the usb stick you use. That being said: I have been able to boot an iso of ubuntu 10.10 (maverick) from a usb stick both on my macbook (1,1) and on my mac mini (first time I get it to boot off of a usb stick at all). [This thread]("http://ubuntuforums.org/showthread.php?t=1504038") has some useful info. But be warned that the process is somewhat convoluted and success isn't guaranteed.

Good luck!

I followed your link, and at the top there was another link which led me to an "updated" version of the tutorial. I browsed through each, and it seems you are right: this can be tricky. It almost seems like the author is half explaining how to make a Live disk, and half explaining an actual install.

I'm working on a 3rd (or 4th maybe) generation MBP...got it about a year and a half ago. I'm trying to install Ubuntu Netbook edition (lightweight, small footprint, sounded perfect for a thumb drive).

Does your assessment account for just USB thumb drives? Or all USB drives? In other words, if I can boot Ubuntu from an external hard drive, should I be able to boot it from a thumb drive? Or are the two treated differently somehow by Mac?

---

### Post by pindar on 2011-02-23
> **teamjh14 said:**
> I followed your link, and at the top there was another link which led me to an "updated" version of the tutorial. I browsed through each, and it seems you are right: this can be tricky. It almost seems like the author is half explaining how to make a Live disk, and half explaining an actual install.

I'm working on a 3rd (or 4th maybe) generation MBP...got it about a year and a half ago. I'm trying to install Ubuntu Netbook edition (lightweight, small footprint, sounded perfect for a thumb drive).

Does your assessment account for just USB thumb drives? Or all USB drives? In other words, if I can boot Ubuntu from an external hard drive, should I be able to boot it from a thumb drive? Or are the two treated differently somehow by Mac?
Yes, I'm not very happy with these half-finished howtos either; he has left at least three different versions in various states of (un)completedness. 

As to your question: I have found that booting any mac from any kind of usb disk without touching your internal disk is tricky and may or may not work, this is true for usb hard disks and for thumb drives. It's fairly easy if you have the /boot partition on your hard disk - but then, the initial aim of your attempt (having a rescue disk) isn't fulfilled; if your internal HD is toast, this wouldn't boot. So basically, you're left with this kind of complex situation. But since the rc for grub2 makes things possible, it may only be a matter of months till this code makes it into distributions, and things will get easier.

---

### Post by Tu1J4kXk8NUhMz on 2011-02-24
Here's a question that's just occurred to me: What is the fundamental reason why one might be able to boot from, say, a USB *hard *drive but not a USB *flash *drive? They seem similar enough, and if a Mac can boot from one, it seems as though you should be able to boot from the other.

This might come across as cynical or sarcastic, but it's not meant to be...I'm legitimately curious. A semi-technical explanation of the differences here would be awesome...if anyone would care to indulge. Please [-o<:-D\\:D/:-k

---

### Post by Tu1J4kXk8NUhMz on 2011-03-03
I would just like to follow up with an update that may help folks (or may not).

Previously, I stated I was able to boot Ubuntu from a USB hard drive (as opposed to a thumb drive). I was wrong. I created a bootable USB hard drive containing installs of Mac OS X 10.6.6 and Ubuntu Netbook 10.10. OS X boots fine (it was created using CCC) while Ubuntu, again, just boots directly to my Windows install. This entire time, I've worked with nothing but Ubuntu Netbook 10.10 (this includes my attempts at create USB live disks).

Strangely enough, I found an article published last night pertaining to this subject on Lifehacker. It's a pretty cohesive rundown of how to do it, but with absolutely no insight on the issue with Macs. For those who'd like to see it, take a look here: [http://lifehacker.com/#!5774997/getting-started-with-linux-how-to-install-linux-on-your-computer]("http://lifehacker.com/#!5774997/getting-started-with-linux-how-to-install-linux-on-your-computer")

I'm still curious to know, from a technical standpoint, why this is (if anyone has some insight). I'd also like to know if this is an issue with the particular distro I'm working with. Might I have better luck with an earlier version of Ubuntu, or a different distro (Mint or Fedora maybe)? Thanks for all the help I've received so far!

---

### Post by B_Free on 2011-03-03
Apparently you own an Intel Mac. I read an article a couple of days ago (but can't find it) that said you can boot from a usb on an Intel machine but never from PPC. Searching these posts [http://mac.linux.be/](http://mac.linux.be/) knows a lot about what you are asking. At the top of the main page of this forum, sticky threads, [http://ubuntuforums.org/showthread.php?t=427714&page=17](http://ubuntuforums.org/showthread.php?t=427714&page=17)
post 169 has your answer.

---

### Post by pindar on 2011-03-03
> **teamjh14 said:**
> I'm still curious to know, from a technical standpoint, why this is (if anyone has some insight). I'd also like to know if this is an issue with the particular distro I'm working with. Might I have better luck with an earlier version of Ubuntu, or a different distro (Mint or Fedora maybe)? Thanks for all the help I've received so far!
I can't give you the technical details, just a few anecdotes from my experience with this (this is all about intel macs):
[LIST=1]
[*]My macbook has a broken CD drive, and I installed some older version of ubuntu on it (I think it was 9.10, but I'm not sure). A few versions ago, ubuntu offered hybrid iso images, and again, I think I could boot the macbook from such a hybrid image which I simply dd'ed to a usb stick.
[*]As far as I can remember, I have never been able to boot the macbook from any usb stick which I prepared with unetbootin or the ubuntu usb creator.
[*]I tried again a couple of weeks ago and spent a couple of hours on this. I now have an 8GB usb stick with rEFIt and grub 1.99.rc1 on it. This boots both my macbook and my mac mini, which I had never managed to boot from any usb device before.
[*]On this usb stick, I have tried booting directly from iso files which I simply copied to the root directory. I have only been able to boot from isos of ubuntu 10.10 and distros which are derived from it (linux mint julia). Neither any other distro nor the alpha of ubuntu 11.04 will boot from this stick even though I use exactly the same commands as for 10.10.
[/LIST]
So there: unfortunately, this is all quite confusing, and it looks like the same stick may boot some, but not all macbooks. The only thing you can do is prepare such a stick and see if it works for you...

---

### Post by Tu1J4kXk8NUhMz on 2011-03-03
I'm fairly certain this has gone from being a curiosity to being my white whale. I spent a lot of time today trying to get this to work...and nothing. I've tried several different configurations, and I got nothing in return. Though from everything I've read, the Ubuntu-supported method works...just not for me I guess.

Perhaps in time, this will become more feasible and less annoying. Thanks for all the help!

---

### Post by mainalisuyog on 2011-03-04
I suffer from the same problem as well. I can boot from a thumb drive. I have installed windows 7 from a thumb drive, and I have also installed ubuntu from a thumb drive. But the problem is, I can install only one. When I have windows and osx installed, the ubuntu thumb drive refuses to boot into ubuntu. Instead, it boots into windows. When I have osx and ubuntu installed, the win7 thumb drive refuses to boot into windows and boots into ubuntu instead. The only solution is to delete the windows partition when i want to install ubuntu, and delete the ubuntu partition when i want to install windows.

---

### Post by dubmartian on 2011-03-04
this info may be outdated but still may be useful/interesting:
[http://www.ibm.com/developerworks/linux/library/l-gpt/index.html](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html)
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

"The Linux kernel must be able to parse GPT data structures in order to                 provide access to the partitions the disk contains. Fortunately, this                 support has long been present in Linux. If you compile your own kernel, be                 sure to check the **EFI GUID Partition Support** item in the                     **Partition Types** area of the **File Systems** configuration                 area, as shown in Figure 1. "

i see options like the following (i think there were more when i did a quick test with 2.6.38-5:
/boot/config-2.6.38-1-generic:CONFIG_EFI_VARS=y
/boot/config-2.6.38-1-generic:CONFIG_EFI_PARTITION=y
/boot/config-2.6.38-1-generic:CONFIG_HFS_FS=m
/boot/config-2.6.38-1-generic:CONFIG_HFSPLUS_FS=m
question  is, is this actually supported in current ubuntu kernels? if it is,  what other configuration is needed? seems to be alot more than changing  the above to = "y" even with a properly configured menuentry booting  with efi x64.

---

### Post by pelle.k on 2011-03-05
[http://ubuntuforums.org/showthread.php?t=869324](http://ubuntuforums.org/showthread.php?t=869324)

---

### Post by srs5694 on 2011-03-05
> **dubmartian said:**
> this info may be outdated but still may be useful/interesting:
[http://www.ibm.com/developerworks/linux/library/l-gpt/index.html](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html)
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

"The Linux kernel must be able to parse GPT data structures in order to                 provide access to the partitions the disk contains. Fortunately, this                 support has long been present in Linux. If you compile your own kernel, be                 sure to check the **EFI GUID Partition Support** item in the                     **Partition Types** area of the **File Systems** configuration                 area, as shown in Figure 1. "

i see options like the following (i think there were more when i did a quick test with 2.6.38-5:
/boot/config-2.6.38-1-generic:CONFIG_EFI_VARS=y
/boot/config-2.6.38-1-generic:CONFIG_EFI_PARTITION=y
/boot/config-2.6.38-1-generic:CONFIG_HFS_FS=m
/boot/config-2.6.38-1-generic:CONFIG_HFSPLUS_FS=m
question  is, is this actually supported in current ubuntu kernels? if it is,  what other configuration is needed? seems to be alot more than changing  the above to = "y" even with a properly configured menuentry booting  with efi x64.

FWIW, I'm the author of the first two sites you reference. The option mentioned in the paragraph you quote is the CONFIG_EFI_PARTITION option, and it's active in recent Ubuntu kernels. (I'm not sure how far back you'd have to go to find an Ubuntu kernel without that option active, if there have ever been any Ubuntu versions released without that version.)

---


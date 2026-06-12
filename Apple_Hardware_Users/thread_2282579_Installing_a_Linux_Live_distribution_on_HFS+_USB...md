---
title: "Installing a Linux Live distribution on HFS+ USB.."
date: 2015-06-15
forum: Apple Hardware Users
---

### Post by datojeremy on 2015-06-15
Hello, please pardon me for my english, I'm French but I do my best!  

Ok guys so here's the catch. I'm a casual Ubuntu user, use it at home... I also use RHEL at work... And for other job related reasons, I may have to use live distributions on a MacBook Air. 

I've been wondering, for security matters, and also just to feed my curiosity, is it possible to divide the usb stick into different partitions, one containing the linux live distrib and the other containing other stuff? Let's say the USB stick is 8Gb and my Linux Iso is ~5Gb, that would be a waist of space... Also my real interrogation is, is it possible that this partition with the live distrib could be formated with HFS+, and only readable by Mac products? So anyone without a Mac would not access the live distribution partition??

Odd question I know, but if anyone has an idea to this, please share, thank you community !!

---

### Post by este.el.paz on 2015-06-17
> **datojeremy said:**
>  Let's say the USB stick is 8Gb and my Linux Iso is ~5Gb, that would be a waist of space... Also my real interrogation is, is it possible that this partition with the live distrib could be formated with HFS+, and only readable by Mac products? So anyone without a Mac would not access the live distribution partition??

Odd question I know, but if anyone has an idea to this, please share, thank you community !!

Probably no is the answer, linux format is not HFS+ . . . 

e..

---

### Post by oldfred on 2015-06-17
I do not see why you could not have a data partition formatted as anything you want.

I have used gpt which may be required for use with a Mac and use grub installed to gpt drive to loopmount the ISO directly. Then I can have more than one ISO on one flash drive.

       Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac - Quackers
[http://ubuntuforums.org/showthread.php?t=2174630](http://ubuntuforums.org/showthread.php?t=2174630)

      
 UEFI only USB key, just copy ISO to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)

 UEFI boot key, loopmount ISO
[http://ubuntuforums.org/showthread.php?t=2257100](http://ubuntuforums.org/showthread.php?t=2257100)

---

### Post by este.el.paz on 2015-06-17
> **datojeremy said:**
>  Also my real interrogation is, is it possible that this partition with the live distrib could be formated with HFS+, and only readable by Mac products? So anyone without a Mac would not access the live distribution partition??

Odd question I know, but if anyone has an idea to this, please share, thank you community !!

@oldfred:

Looks like a lot of good data . . . I don't know enough about moving iso's to USB . . . not sure if the OPs question is addressed by this data?  They only want people with Mac to be able to "access the live [linux] distribution partition" . . . .

e..

---

### Post by datojeremy on 2015-06-18
> **este.el.paz said:**
> Probably no is the answer, linux format is not HFS+ . . . 

e..

Aren't Fat32 or Ntfs Linux format ? But thank's, I'll just try classic partitions I guess

> **oldfred said:**
> I do not see why you could not have a data partition formatted as anything you want.

I have used gpt which may be required for use with a Mac and use grub  installed to gpt drive to loopmount the ISO directly. Then I can have  more than one ISO on one flash drive.
 

Sounds like a pretty good solution, I'll try this! Although, I only need one bootable iso on a usb flash drive and regular data on the other partition.

Seems like booting on Hfs is not quite possible so I'll drop the idea, thank you all for your sharing!

---


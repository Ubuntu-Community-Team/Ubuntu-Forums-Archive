---
title: "Windows 8 on SSD + internal HDD (currently without OS): how-to dual-boot?"
date: 2013-06-10
forum: Any Other OS
---

### Post by TheStoof on 2013-06-10
I consider myself to be a novice when it comes to Unix, and I'm interested in not ruining my partitions like I have done several times before. 

My current set-up is with a Samsung laptop with an Samsung SSD using UEFI with the DVD swapped with the old internal HDD that is currently without an OS and used only as a data drive. I'll shrink the partition to make room for Ubuntu. The mount point would be set to / and a swap partition created to be 8192 MB in size.

How do I properly update Windows 8's boot config to see Ubuntu on the other internal HDD?

---

### Post by oldfred on 2013-06-10
Will your system boot from the hard drive? Many systems seem to not boot from a drive that is used in place of the DVD.

Also if Windows is UEFI, then you need to install Ubuntu in UEFI boot mode to easily dual boot. Otherwise you have to go into UEFI/BIOS and change boot mode each time you want to change boot. Not easy way to dual boot.

And to install Ubuntu in UEFI mode, your old data drive has to be gpt partitioned. If an older drive it probably is MBR(msdos). 

I have not attempted to convert a drive.
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

   Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

See my signature for info on UEFI issues.

---

### Post by irv on 2013-06-13
Oldfred helped me out with this, almost the same as what you are trying to do. First you need to go into you computer setup and turn off secure boot and fast boot. You can boot into UEFI boot mode, then go back into Windows 8. Go to setting and select "Change PC Setting". It is located just below Power and Keyboard. Then select "General", in the left pane and scroll down to the bottom of the right pane and click on restart. It will give you the option to select what you want to boot. USB, CD/DVD. You then can boot into Ubuntu if it is installed on a USB or DVD. 
I was booting a live USB and it booted just fine, the problem I had was installing it on a external USB SSD. But if all you want to do is run it from a different drive you might just have an option to do this from the restart under general.
I did hear where some systems will not boot into Windows 8 with secure and fast boot turn off, but on my Asus Q500A it boots just fine.

---


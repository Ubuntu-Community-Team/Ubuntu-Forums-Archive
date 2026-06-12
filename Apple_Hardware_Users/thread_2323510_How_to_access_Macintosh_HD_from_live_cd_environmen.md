---
title: "How to access Macintosh HD from live cd environment"
date: 2016-05-05
forum: Apple Hardware Users
---

### Post by issh on 2016-05-05
Hello, I am working on someone's 2011 iMac with intel processor. Their iMac boots with a kernel panic and it will not proceed further. I am now trying to recover data from the hard drive labelled, "Macintosh HD" but, I don't have permissions to access it. I don't want to write to the hard drive, only read and copy from. 

How do I go about doing this? 

iMac specifications:

2011 iMac
Mac OS X 10.8
3.9GB RAM
Intel Core 2 Duo CPU E7600 @ 3.06GHz x2
Graphics: Gallium 0.4 on AMD RV730 (DRM 2.43.0, LLVM 3.8.0)

Live CD is Ubuntu 16.04 32bit i386

I'm comfortable using a terminal. Please, help would be appreciated. Thank you in advance. 

#Urgent

---

### Post by QIII on 2016-05-05
Moved to Apple Hardware Users.

You'll probably get better help here.

---

### Post by issh on 2016-05-06
I have an update for anyone who may need this and hopefully someone else will offer some help.

I was able to access the "Macintosh HD" from an Ubuntu 16.04 i386 disc using the command:

[I]sudo nautilus

[/I]in a terminal. Note: you have to run two *sudo nautilus *commands from a terminal as super user. Leave one window open and and use the second window to navigate the "Macintosh HD."

However the optical super drive on the 2011 iMac has quit working. 

So now I've had to make a live usb to boot from for the iMac. 

uNetbootin or any other tools will not make a live usb that will work on an iMac or any other recent Macs. However there is a solution! 

I found help here: 
[U]
*[https://sevenbits.github.io/Mac-Linux-USB-Loader/](https://sevenbits.github.io/Mac-Linux-USB-Loader/) *[/U]and here _*[http://www.linux.org/threads/mac-linux-usb-loader.3579/]("https://www.linux.org/threads/mac-linux-usb-loader.3579/") *_and here _*[https://www.maketecheasier.com/create-linux-live-usb-in-mac/](https://www.maketecheasier.com/create-linux-live-usb-in-mac/)*_

I had to load the USB drive manually because I do not have a working iMac to run the application, "Mac Linux USB Loader" on. In case sharing of links aren't allowed I will detail instructions below. If you have a working, compatible iMac simply run the "Mac Linux USB Loader" which is OpenSource, on your machine and it will do the work for you. 

I also need help with an error loading the bootable .iso after these instructions if anyone can please help me. I think it's something wrong with the Ubuntu .iso image so hopefully you guys can help me. 

First, you need to determine if your iMac is either a 64 bit machine or 32 bit machine. Once you've determined what bit your machine is... Second, download the package "Mac Linux USB Loader." Either download from the above link or do a search on the interwebz. If you are on a PowerPC Mac like I am or on a Windows PC you can open the package and search for the files you need manually. (You may need a program such as 7zip or similar to access the package. You need to get the .efi files called "bootiax32.efi" or "bootx64.efi." Please note that some versions of the application "Mac Linux USB Loader" use the 32 bit efi loader with a different name, but it should still work. It could also be called just simply "boot.efi" which would also work in place of "bootiax32.efi." Now, grab your linux distribution of choice and rename it as "boot.iso" sans quotes. Format your USB drive as FAT or if you're on a Mac machine, use disk utility and format the drive as MS-DOS. Then inside the USB create a folder tree in this scheme:

[I]/EFI/BOOT

[/I]Place both the .efi file and the boot.iso image inside the BOOT folder. Safely eject the drive and plug it into the problem iMac (Or leave it in the USB port if the Mac machine you're working on also happens to be the one you're using) and restart the iMac while pressing the "Alt" key. You'll be presented with a selection of bootable drives to choose from. 

Now here is my problem. When I selected and tried to boot the live usb drive it presented with these errors:

[I]Error: can't find configuration file
[/I][I]Error: configuration file parsing error
[/I][I]Error: can't find GRUB boot loader

Cannot continue because core files are missing or damaged

[/I]Can someone please help me? Is this a problem with the Ubuntu 16.04 .iso?

---


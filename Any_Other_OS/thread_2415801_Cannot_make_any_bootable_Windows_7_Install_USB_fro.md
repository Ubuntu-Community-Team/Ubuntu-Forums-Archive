---
title: "Cannot make any bootable Windows 7 Install USB from Ubuntu Linux."
date: 2019-03-31
forum: Any Other OS
---

### Post by nerv-agent on 2019-03-31
A continuation of this [unresolved hot mess]("https://ubuntuforums.org/showthread.php?t=2415098").

I downloaded a legitimate Windows 7 ISO from Microsoft with my license key.

I changed my BIO settings as described here (I'm on a Dell Precision 7520 laptop):

[https://www.dell.com/support/article/us/en/04/sln302339/downgrade-to-windows-7-professional-edition-on-a-system-shipped-with-windows-10-professional?lang=en#Change-System-Setup](https://www.dell.com/support/article/us/en/04/sln302339/downgrade-to-windows-7-professional-edition-on-a-system-shipped-with-windows-10-professional?lang=en#Change-System-Setup)

I used WoeUSB to make a bootable USB drive, got an error.

I right clicked on the ISO file itself and used Disc Image Writer and it *seemed* like it made a bootable drive.

I try booting from it, and I keep getting the error:

"Selected boot device failed."

I called Dell technical support and they told me to change the BIOS settings which I already did. Ultimately, they couldn't help me and I wasted time with that phone call.

I've been scouring Google all day and keep finding "solutions" that don't even work.

How do I install Windows 7 from a USB drive on a modern motherboard?

Just wasted my entire Sunday dealing with this when I was supposed to be visiting family this weekend.

That 2019-03-15 update has disrupted so much of my free time in an attempt to fix this mess that I'm seriously thinking of using Windows 10. And that sickens me.

I have a splitting headache right now.

---

### Post by oldfred on 2019-03-31
UEFI or BIOS hardware. Note all systems since 2012 are UEFI since Microsoft required Windows 8 to be installed in UEFI boot mode.
Windows 7 update now includes UEFI boot, older versions had to be copied to flash drive & a couple of files moved/renamed.
How you boot install media UEFI or BIOS is then how it installs.
But Windows only installs to gpt partitioned drives in UEFI boot mode and only to MBR partitioned drives with BIOS. 
So settings in UEFI/BIOS, drive partitioning, boot mode of installer all have to match UEFI or BIOS.

If you have the Microsoft version, you also may need additional drivers, often downloadable from your vendor.

These are all in 7000 series & issues are often common across many models. Often bigger difference if AMD or Intel based system.
       DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359) 
    
       Make Windows bootable installer from Ubuntu
[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)
[https://ubuntuforums.org/showthread.php?t=2328513&p=13557011#post13557011](https://ubuntuforums.org/showthread.php?t=2328513&p=13557011#post13557011)
[http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-using-ubuntu)
 How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition](https://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition)

---

### Post by nerv-agent on 2019-03-31
I keep seeing this "Rufus" program mentioned in various search results and even in the links in your post. But it looks like it's a Windows program.

Is there a Linux equivalent? Kinda wary about using WINE....

Also, in the "onetransistor" article, they use the command line:

sudo grub-install --target=i386-pc --boot-directory="/media/<username>/<drive_label>/boot" /dev/sdX

But would the "target=i386-pc" be different if I am using a 64 bit OS (both Ubuntu and Windows in 64-bit)?

---

### Post by oldfred on 2019-03-31
The i386-pc is for BIOS boot.

If you just want UEFI, I think this works for both Ubuntu & Windows as UEFI boots from a file at /EFI/Boot/bootx64.efi and ISO has that file.
       UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
[https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)

---

### Post by C.S.Cameron on 2019-04-01
Sometimes it is best to use a Windows tool for a Windows product. Windows USB Tool works for installing Windows 10.
[https://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool](https://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool)

But, you may need a friend with Windows.

---

### Post by nerv-agent on 2019-04-02
Uhhhh, the Microsoft Windows tool doesn't run under Linux. It's for Windows.

---

### Post by nerv-agent on 2019-04-09
Oh no. 

 So I re-enabled UEFI boot and followed the "onetransistor" article.  I was able to boot, but the setup gets stuck because it says something like "windows 7 install cd/dvd drive device driver is missing". I did some research and it has something to do with USB 3.0 drivers not being included in the installation disc.  

So I put "Intel-USB-eXtensible-Host-Controller-Driver_FW1H3_WIN_5.0.4.43_A04.EXE" in the root directory of the USB disk, BUT IT DOESN'T DETECT IT!  What am I doing wrong?

---

### Post by robfeight on 2019-08-20
nerv-agent, I am experiencing the spot-on same situation. Fortunate for you you only seem to have a day tied into it. I'm at around three months. A new battery, later. A new hdd, later. Official Windows 7 download. Alternative Windows 7 source download. Three different USB flashdrives. An SD card. Multiple different USB bootload maker options, such as, WoeUSB, GParted, mount the ISO, copy files over, rename a bootx64.efi file, copy, paste, open up install.wim--or, whatever the crazy ./1/Windows/eti/boot zip file was that I had to fish bootmgfw.efi out from was....and on....and on...

Absolute insanity.

Kicker for me is that I worked for five years repairing computers. I've reinstalled Windows probably three hundred to six hundred times. Taught computer maintenance classes. I've brought computers back from the dead. Ubuntu is new to me, though. Paired with all these different partition table options, partition format options, grub, eti, et cetera, and it's a damned nightmare. Pure terror.

In any case, I didn't notice if you finally found a solution for this issue. I'll re-comb through this thread, but just in case, let me know if you did.

---

### Post by oldfred on 2019-08-21
Is still worth fighting Windows 7 for just a few months?
       Windows 7 End of Life - January 2020 

It was my understanding that the original Windows 7 ISO required file copy & move to boot in UEFI mode. But the updated Windows 7 ISO was UEFI bootable without the copy effort.

Newer Windows ISO are now over 4GB and cannot be booted from one FAT32 partition on USB flash drive. The UEFI boot files have to be in the FAT32 partition, but rest of install has to be in a NTFS partition on flash drive.

---

### Post by oldfred on 2019-11-05
@janinababa776
If tools posted do not work in a Mac, then best to ask in the Apple Mac sub-forum where those who know Mac should respond. 
[https://ubuntuforums.org/forumdisplay.php?f=328](https://ubuntuforums.org/forumdisplay.php?f=328)

Otherwise a Windows forum or Mac forum.

---


---
title: "Installing Ubuntu to an External Hard Drive to run on Mac 2008"
date: 2014-03-11
forum: Apple Hardware Users
---

### Post by tiffany3 on 2014-03-11
iMac (7,1) mid-2007 running Maverick 10.9.2
2.8GHz Intel Core 2 Duo Extreme x7900
4GB 667 MHz DDR2 SDRAM
ATI RADEON 2600 Pro [COLOR=#000000]with 256MB of GDDR3 memory

*According to something you can run in terminal, my computer is 64EFI 
[/COLOR]
Downloaded Ubuntu 12.04 LTS for 32bit 
Downloaded Ubuntu 12.04 LTS 64bit
Downloaded Ubuntu 13.04 AMD64
Downloaded Ubuntu 13.04 32bit
Downloaded Ubuntu 64AMD+mac
Downloaded Mac Linux USB Bootloader
Downloaded rEFInd
Downloaded Grub2
Downloaded syslinux 5 
Downloaded syslinux 6
Downloaded unetbootin

1. I installed rEFInd to my computer using the install.sh. 
2. I used Mac Linux USB bootloader to create a Ubuntu Live USB bootloader.
3. I burned the Ubuntu 12.04 32bit Live USB to a disc.  
4. I start up computer holding the option key, then I choose the disc.
5. Ubuntu opens. 
6. I choose install Ubuntu
7. I choose "something else", partition external hard drive 

/dev/sbb Seagate GoFlex 2.0TB
/dev/sbb1 /boot 500MB
/dev/sbb2 /       5GB
/dev/sbb3 swap 4GB
/dev/sbb4 fat32 ~11GB 

Ubuntu tells me installation complete, please restart your computer. I restart computer. 

I see two options on the rEFInd screen:
Apple (boot Mac OS X from pandorica - my internal drive) Linux (boot Linux from Partition 3 - my external drive)
Choose Linux aaaannnd:

Warning: Attempt to load icon of the wrong size from '\.VolumeIcon.icns'
Starting legacy loader
Using load options "USB"
Error: Not Found returned from legacy loader
Error: Not Found from LocateDevicePath... (this is repeated 7x)
Error: Load Error while (re)opening our installation volume

The firmware refused to boot from the selected volume. Note that external hard drives are not well-supported by Apple's firmware for legacy OS booting. 

OK. Well I can get to Ubuntu if I put the Ubuntu Live USB and rEFInd directly onto the hard drive with no Ubuntu partitioning, but doing it that way, I get: 

Available boot options
1) Boot Linux from ISO file
2) Modify Linux kernal boot options (Advanced!)

I choose option 2, which then gives me a screen of more options of which I choose option 3) no efi, and option 9) no gpt

Then, I get a screen that says: 

kernal path: /casper/vmlinuz |ramdisc 
noefi nogpt
load linux
path: /casper/initrd.lz
loading linux kernal...
loading initial RAM disc...
Booting in blind mode


Ubuntu opens up. Great except I won't be able to get Network Connectivity because the drivers won't stay downloaded.  

The above has gotten me the closest.

I'm on day 3 of trying to get this installed to an external hard drive. That's all I want! To be able to turn on my Mac, hold down the option key, see the Ubuntu icon in the rEFInd screen, choose it, and have Ubuntu open up...and I'm able to get online as well. 

I just don't get it. I've downloaded so much because I've tried numerous different approaches. I have read and read and read different approaches, forum questions; watched videos, etc. I don't mind using terminal for some stuff, but it seems that using terminal is if I want to dual boot my internal hard drive, which I do not. And honestly, most of what I've read wasn't terribly clear on WHERE do I type this or that? The Mac terminal? The Ubuntu terminal? What am I missing?

---

### Post by tiffany3 on 2014-03-11
After posting this, I tried again...

Erased external hard drive and created one partition with MS-DOS Fat Format. When partitioning my hard drive in Disk Utility, there is an Options button that I clicked on to change my hard drive partitioning scheme. Choices are: GUID, Apple Partition Map, or MBR for Master Boot Record. Keep the GUID option selected. I don't understand why, I kept reading that it needed to be MBR, but GUID worked. 

Shut down computer and restarted with Ubuntu 13.04 AMD64 LiveCD (I figured, why not? what have I got to lose?). GNU pops up and I chose to Try Ubuntu. Now, here is where I believe I was getting lost in translation: everything I was reading was telling me to download this and that, now do this and that in terminal... finally, under the Ubuntu Apple Sticky did I see that GPartition is installed in Ubuntu. After my initial partitioning, I needed to partition again! But that sticky is pretty old so once I got past the partitioning part, which is still relevant, I watched this video...[https://www.youtube.com/watch?v=KDM2LqFoHv4](https://www.youtube.com/watch?v=KDM2LqFoHv4). I installed Ubuntu, and finally! I am able to start up through rEFInd, choose Ubuntu, and have Ubuntu WORK. Also, I'm finally online :)

---


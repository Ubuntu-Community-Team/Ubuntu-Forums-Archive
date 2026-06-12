---
title: "GRUB loader and USB Wireless"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by briandoherty on 2006-03-02
I had Ubuntu running within VMware for windows for awhile, but in an effort to convert me over to linux and for extra performance, I installed Ubuntu on an old 10GB hard drive. I unplugged my other 2 hardrives when I installed, just to be safe. When I plug them back in Ubuntu notices both of them in the Disk's section of the Administration pull down. However in the GRUB loader it hasn't automaticy detected my windows install. I've tryed editing the grub config file by copying and pasting some of the examples in there for XP, and editing the root path. It doesn't work.

I have XP installed on a Serial ATA drive, and a 2nd slave for storage. Since GRUB is only on my 3rd hardrive, I boot to that. Nothing in the GRUB loader gave me anything for XP, and my tweaks to the config file didn't help. I figured I could always just change the boot order of the hard drives to get to XP again, but I get a system disk error when trying to do that, and so I think getting GRUB loader working correctly is the only way to let the 2 OS's live in peace. The only way I can boot into windows now is disconnecting the 3rd hard drive. On my IDE1 I have a DVD/RW, and my storage hard drive (no OS).     On my IDE2 I have my 3rd hard drive (Ubuntu). On my Serial ATA I have my 1st hardrive (XP). I think that will help you guys determine my root directory? Sorry for the terrible explanation, I can't look right at my install and show you, as Ubuntu internet access doesn't work, which leads me to my next problem. 

I have USB wireless adapter. It's a  Hawking HWU54G USB Adapter. I assumed that perhaps the Ubuntu install wouldn't pick it up, and I'd have to fix things later. I went into the Network settings but Ubuntu hasn't even detected the USB as a network adapter. I see an ethernet option, and a modem one. Both don't give me results. If I can fix this problem, I may be able to provide for visuals for the above problem. 

Sorry for the really newbie questions, I've just come across Linux in the past month or so and I'm intriuged by it, thanks!

---

### Post by Pragmatist on 2006-03-03
How are you booting the linux drive (the third one)?  Did you set the boot order in the BIOS to boot the third disk first?

make a text file in Ubuntu and put the following in it (then you could save to disk, bring to your online machine and give it to us as an attachment:

1.) /boot/grub/menu.lst
2.) dmesg

To do this, go into a terminal (konsole in KDE; gnome-terminal in GNOME) and mount your floppy drive:
```
sudo mount /dev/fd0 /media/floppy
```
```
cd /media/floppy
```
```
sudo cat /boot/grub/menu.lst > output_file
```
```
dmesg >> output_file
```
```
sudo umount /dev/fd0
```
Now you have a file called **output_file** which you can attach here

---

### Post by Brunellus on 2006-03-03
[QUOTE=briandoherty]I had Ubuntu running within VMware for windows for awhile, but in an effort to convert me over to linux and for extra performance, I installed Ubuntu on an old 10GB hard drive. I unplugged my other 2 hardrives when I installed, just to be safe. When I plug them back in Ubuntu notices both of them in the Disk's section of the Administration pull down. However in the GRUB loader it hasn't automaticy detected my windows install. I've tryed editing the grub config file by copying and pasting some of the examples in there for XP, and editing the root path. It doesn't work.

I have XP installed on a Serial ATA drive, and a 2nd slave for storage. Since GRUB is only on my 3rd hardrive, I boot to that. Nothing in the GRUB loader gave me anything for XP, and my tweaks to the config file didn't help. I figured I could always just change the boot order of the hard drives to get to XP again, but I get a system disk error when trying to do that, and so I think getting GRUB loader working correctly is the only way to let the 2 OS's live in peace. The only way I can boot into windows now is disconnecting the 3rd hard drive. On my IDE1 I have a DVD/RW, and my storage hard drive (no OS).     On my IDE2 I have my 3rd hard drive (Ubuntu). On my Serial ATA I have my 1st hardrive (XP). I think that will help you guys determine my root directory? Sorry for the terrible explanation, I can't look right at my install and show you, as Ubuntu internet access doesn't work, which leads me to my next problem. 

I have USB wireless adapter. It's a  Hawking HWU54G USB Adapter. I assumed that perhaps the Ubuntu install wouldn't pick it up, and I'd have to fix things later. I went into the Network settings but Ubuntu hasn't even detected the USB as a network adapter. I see an ethernet option, and a modem one. Both don't give me results. If I can fix this problem, I may be able to provide for visuals for the above problem. 

Sorry for the really newbie questions, I've just come across Linux in the past month or so and I'm intriuged by it, thanks![/QUOTE]
USB wlan adaptors are notoriously problematic with Linux.

[this page](http://www.linuxquestions.org/hcl/showproduct.php/product/2891/sort/2/cat/160/page/1) reports that it can work in Linux, provided you install the necessary driver.  Another quick Google reveals that there are drivers available for download [here](http://zd1211.ath.cx/).

---

### Post by briandoherty on 2006-03-06
Here you go, it didn't work in the command line quite as well because apparently I didn't have authority to output_file, and my su root did not work, but I worked around my problem.

---

### Post by Pragmatist on 2006-03-06
Since SATA is relatively new, I'd like to be sure about how Linux is naming your devices. Please give the output of:
```
sudo mount
```
```
cat /etc/fstab
```

---


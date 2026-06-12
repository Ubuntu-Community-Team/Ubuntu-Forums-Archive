---
title: "Triple Boot rEFIt-GRUB"
date: 2011-01-17
forum: Apple Hardware Users
---

### Post by kazuki89 on 2011-01-17
Hi, this is my first message. 
I installed a triple boot on my MacBook 5,1 with Snow Leopard, Windows 7 and Ubuntu 10.10 Maverick using this guide: 

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Now I've a problem. When, from rEFIt, I boot in Mac OS everything is ok. While, when i boot in Ubuntu or in Windows both run GRUB and then i have to choose between Windows and Ubuntu.

I'd like to enter directly in Windows when I choose it from rEFIt and not to start GRUB before it.

How I can do this?

Sorry for my English: I'm Italian.

Thank you to everybody.

---

### Post by sudo_0 on 2011-01-17
your english is good :)

i'm actually having the same problem (kind of)

when i boot it automatically goes to the grub after about 30 seconds of blank screen... 

i don't mind the wait because i'm usually doing a few things when i first boot up anyway...


i do know that when doing a triple boot you have to install windows last or it won't boot correctly but that could just be random information to you.

but bump for answers. :)

---

### Post by kazuki89 on 2011-01-18
Thanks. So I'll try to install Linux for first. And then I'll post the results.

---

### Post by FireLizzard on 2012-01-27
The Windows installer writes the windows bootloader to the mbr. 'grub-install /dev/sda' or suchlike writes grub to the mbr. Only one thing can be in the mbr. To avoid this, you can try to install grub to a partition, but that can be tricky.

The following won't work in Mac OS, and can do very band things to your drive if not done right. If you want to save your MBR so you can 'undo' any mistakes (aka, overwriting the windows bootloader), run the following command:
```
sudo dd if=/dev/sda of=<somefile> bs=512 count=1
```
This will save the MBR of the first drive to the file <somefile>. Note that this will not work on a partition (sda1, sda2, etc). Run the following to restore your mbr to your HD:
```
sudo dd if=<somefile> of=/dev/sda bs=512 count=1
```
When running this last command, be careful not to change anything, unless you know what you are doing. This command writes <somefile> to the first sector of your HD, clobbering whatever might have been there (the MBR almost certainly). If you write gibberish here, Windows and/or grub will no longer boot (without other tools like UBCD). Make sure <somefile> is the same file you created with the first command.

Theory:
The first sector of your drive is your MBR. As far as I know, all modern HD's have a sector size of 512 bytes. Thus, the first 512 bytes of your drive are your MBR. Your MBR stores the BIOS bootloader and partition table for your HD.
The command 'dd' performs a byte for byte copy. 'if' stands for input file. 'of' stands for output file. 'bs' means block size and 'count' specifies how many blocks of size bs the command will copy. When the output file is your HD (/dev/sda), you are writing to your HD and can break things if you are not careful. To read or write your MBR, you want the first 512 bytes of your HD, so bs * count = 512 is necessary. Simply, 'bs=512 count=1' or 'bs=1 count=512'. If you leave off count, the command will read or write until it reaches the end of your hard drive (bad). Both of these commands should end quickly and output on of the following:

'bs=512 count=1':
```
1+0 records in
1+0 records out
512 bytes transferred in 0.019265 secs (26576 bytes/sec)
```
'bs=1 count=512':
```
512+0 records in
512+0 records out
512 bytes transferred in 0.022546 secs (22709 bytes/sec)
```

---

### Post by tgeulin on 2012-01-29
> **kazuki89 said:**
> Hi, this is my first message. 
I installed a triple boot on my MacBook 5,1 with Snow Leopard, Windows 7 and Ubuntu 10.10 Maverick using this guide: 

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Now I've a problem. When, from rEFIt, I boot in Mac OS everything is ok. While, when i boot in Ubuntu or in Windows both run GRUB and then i have to choose between Windows and Ubuntu.

I'd like to enter directly in Windows when I choose it from rEFIt and not to start GRUB before it.

How I can do this?

Sorry for my English: I'm Italian.

Thank you to everybody.
use a tool on mac called gdisk to recreate your hybrid mbr table
check out [http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210) for more information.

---


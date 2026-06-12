---
title: "Unable to Install Ubuntu late 2007 Macbook pro"
date: 2019-01-03
forum: Apple Hardware Users
---

### Post by tomreid on 2019-01-03
Hi all, hoping someone can help me. 

I have a Macbook pro I have now been using since November 2007. I always wanted to replace Mac OSX with Ubuntu when the time came that the OSX version it would take was no longer supported. 

However I have got stuck today. When booting from the bootable USB stick I made of the latest 64bit Ubuntu LTS, I get as far as "try ubuntu without installing it" at the first GRUB menu. When I select this option, the screen goes blank and nothing else ever happens. I can hear the system's fan working quite hard whilst I'm looking at the blank screen, which makes me think that maybe it's doing something I can't see which maybe points to a Graphics card compatibility issue? it's running a Nvidia card, and i tried this workaround I found here but to no avail: *[https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733](https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733)*

 [SIZE=1]*[COLOR=#101010][FONT=&quot]Modifying the GRUB Boot Loader Command[/FONT][/COLOR]*[/SIZE][COLOR=#101010][FONT=&quot]
[LIST=1]
[*][SIZE=1]*Shut down your Mac by pressing and holding the **Power** button.*[/SIZE]
[*][SIZE=1]*Once your Mac shuts down, restart and return to the **GRUB boot loader screen** using the instructions above.*[/SIZE]
[*][SIZE=1]*Select **Try Ubuntu without installing**, but do not press the Enter or Return key. Instead press the **'e' key** to enter an editor that will allow you to make changes to the boot loader commands.*[/SIZE]
[*][SIZE=1][I]The editor will contain a few lines of text. You need to modify the line that reads:
[/I][/SIZE][SIZE=1]*linux/casper/vmlinuz.efi file=/cdrom/preseed/Ubuntu.seed boot=casper quiet splash ---*[/SIZE]
[*][SIZE=1]*Between the words 'splash' and '---' you need to insert the following:nomodeset*[/SIZE]
[*][SIZE=1][I]The line should end up looking like this:
[/I][/SIZE][SIZE=1]*linux   /casper/vmlinuz.efi file=/cdrom/preseed/Ubuntu.seed boot=casper quiet splash nomodeset ---*[/SIZE]
[*][SIZE=1]*To make the edit, use the **arrow keys** to move the cursor to the location just after the word splash, then type '**nomodeset**' without the quotes. There should be a space between splash and nomodeset as well as a space between nomodeset and ---.*[/SIZE]
[*][SIZE=1]*Once the line looks correct, press **F10** to boot with the new settings.*[/SIZE]
[/LIST]
[/FONT][/COLOR]
The system spec is:

2.6 GHZ Intel Core Duo
4 GB RAM
around 100 GB Spare SSD Space

I did (in around 2009) get Ubuntu working well on a very similar system. But now am completely stuck. Hope someone can help.

Thanks

Tom.

---

### Post by mwei19 on 2019-01-03
The ***nomodeset*** worked for me when I was installing the OS on my mid 2010 macbook pro. 
Another thing you can try is to remove the ***quite splash*** in the grub menu and just have that ***nomodeset*** there so that way the screen should show you what it is doing/what it is failing on? 
I actually just removed the quite splash all together after I got the OS up and running as well, just so I can kind of sort of see what is going on during the boot up. 

something like this:
[SIZE=2]**[FONT=arial]*linux /casper/vmlinuz.efi file=/cdrom/preseed/Ubuntu.seed boot=casper [COLOR=#ff0000]nomodeset[/COLOR] ---*[/FONT]**[/SIZE]

---


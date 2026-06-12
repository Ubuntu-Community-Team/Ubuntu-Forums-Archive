---
title: "Usb, write protected? Help! Broken..."
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by nebriv on 2007-05-16
ok... I am kinda new to this stuff but I think I am half way decent with computers. But anyways I was trying to write ubuntu to my usb flash drive using this guide [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
Now obviously things didn't go so well....
I tried formatting my flash drive and fixing it but it won't let me. I just errors of all sorts.  I booted into windows and I got the cannot format, device is write protected. I have no clue what to do. I tried chmod"ing" it to 777 and 666, that didn't work, i tried dragging the contents of the drive into the trash...they just came back....I tried shredding it but that just came with tons of errors. PLEASE HELP! basically I am unable to use my flash drive! 

Thanks in advance

---

### Post by adampyre on 2007-05-16
How are you attempting to format it? Did you just want to start from scratch?

---

### Post by smoker on 2007-05-16
if you open nautilus as root, you should be able to do what you want with the files on your drive:

alt+f2, then 'gksudo nautilus' without the quotes,

best of luck

---

### Post by bodhi.zazen on 2007-05-16
Not to ask the obvious, but does your usb drive have a switch on it that converts it to write protected ?

---

### Post by nebriv on 2007-05-16
ok hang on I will try the naltuilus thing... no its doesn't have a switch... i checked like 4 times ;) just to make sure

---

### Post by nebriv on 2007-05-16
I just want to start from scratch...as in just format it...erase everything off it. then format it with a fat 32 or 16 partition so i can use it again

---

### Post by nebriv on 2007-05-16
i don't think the naultilis thing worked...

---

### Post by nebriv on 2007-05-16
i tried deleting a file on the flash drive while in sudo with natutlis and I got

[CENTER]Error while moving[/CENTER]
 "/media/edgy...yslinux.cfg" cannot be moved because it is on a read-only

---

### Post by nebriv on 2007-05-16
hehehe another update...looking at the edgy folder (the partition) i see a little lock symbol...:( is that bad?

---

### Post by bodhi.zazen on 2007-05-17
> **nebriv said:**
> hehehe another update...looking at the edgy folder (the partition) i see a little lock symbol...:( is that bad?

No, the lock typically means you do not have write permissions.

---

### Post by nebriv on 2007-05-18
so how do I make it so I do have write permissions?

---

### Post by mediax on 2007-05-18
I've had a similar problem with an MP4 player and was informed that if your USB is formatted as FAT, then it doesn't recognise permissions which means that chmod doesn't work.

If you unmount it and then remount as a read-write device that should solve your problem.  I wish I could give you the exact wording for the mount command you need, but I'm not that proficient (yet)!

Good luck!

---

### Post by nebriv on 2007-05-18
ahh man...great! Thanks I will try it as soon as I can!...I hope it works...If anyone has any ideas on how to remount it with permissions it would be helpful so I don't need to find the commands etc! THANKS!

---

### Post by nebriv on 2007-05-18
uhhh okay...turns out I have no clue where to start mounting the flash drive...I know how to un mount not mount :( PLEASE HELP!

---

### Post by nebriv on 2007-05-18
please help...

---

### Post by nebriv on 2007-05-19
come on people! please help... :(

---

### Post by bodhi.zazen on 2007-05-19
> **nebriv said:**
> come on people! please help... :(

Depends of the file system:

Mount Windows: [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

Mount Linux : [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by nebriv on 2007-05-19
yes but mounting it with the read write permissions

---

### Post by Campingman on 2007-05-19
I had a similar problem with read / write permissions on an sd card recently.  The only way I could get Ubuntu to accept the card was to format with gparted.  After that hey presto I could read /write OK.  The SD card still will not mount automatically but that is another topic I guess.  It may be different for you but worth a try I guess.  Back up any data (if you can) and format to FAT with Gparted in Ubuntu.
[http://ubuntuforums.org/showthread.php?p=2545785#post2545785](http://ubuntuforums.org/showthread.php?p=2545785#post2545785)
There may be something in the thread that will help

---

### Post by nebriv on 2007-05-19
i can't format it, thats the problem

---

### Post by Campingman on 2007-05-19
Apologies nebriv, I should have read your thread fully.  If you have access to windows you could try this utility listed (HP usb format)
[http://www.pendrivelinux.com/2006/09/19/all-in-one-usb-pclinuxos-minimezip](http://www.pendrivelinux.com/2006/09/19/all-in-one-usb-pclinuxos-minimezip)

---

### Post by Campingman on 2007-05-19
You do not say what make of pen drive this is?  This seems to be a problem experienced with a few different makes of drive.  I have googled a bit as I am intrigued, there a few dos utilities listed that may help you,  It can also be caused by corruption due to unsafe removal of the drive.  Looking at a few threads on different sites it is unresolved in most cases.  You have probably found most of these already but here goes, one may help you.
[http://www.hardwareanalysis.com/content/topic/46202/](http://www.hardwareanalysis.com/content/topic/46202/)
[http://www.hardwareanalysis.com/content/topic/35725/](http://www.hardwareanalysis.com/content/topic/35725/)
[http://www.askmehelpdesk.com/other-hardware/how-disable-write-protected-128-mb-pen-drive-frontech-12896.html](http://www.askmehelpdesk.com/other-hardware/how-disable-write-protected-128-mb-pen-drive-frontech-12896.html)
[http://www.computing.net/hardware/wwwboard/forum/33941.html](http://www.computing.net/hardware/wwwboard/forum/33941.html)
[http://www.uwe-sieber.de/usbstick_e.html](http://www.uwe-sieber.de/usbstick_e.html)
Hope you get it sorted

---

### Post by nebriv on 2007-05-23
argh nothing....maybe my flash drive is corrupt...I don't know why it would be...GAH!!!

This is really annoyying...Thanks for the links campingman

---


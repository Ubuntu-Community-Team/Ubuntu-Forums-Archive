---
title: "MacBook 2,1 (late 2006) and Ubuntu 14.04 LTS"
date: 2014-05-08
forum: Apple Hardware Users
---

### Post by Oliver_Bell on 2014-05-08
Hi All,

I've been an Ubuntu user for a long time, but this is my first post on these forums. My question is;

Has anyone had any success installing Ubuntu 14.04 from DVD on one of these MacBooks, and are they still supported by Ubuntu?

I've had Ubuntu as the main system on it since the release of 10.04 LTS, and it currently has 12.04 LTS installed. I've never had any problems with installations in the past, and was hoping to do a fresh install and put 14.04 LTS on it.

The install DVD gets as far as the "Try Ubuntu" / "Install Ubuntu" / "Check disks for errors" etc. screen (dark purple screen with white writing). I am able to scroll through the available options, but upon selecting one of the options by pressing the enter key, the installer becomes unresponsive.

Has anyone had any success with these MacBooks? Are they still supported, or should I stick with 12.04?

Thanks in advance!

Oliver

---

### Post by gordintoronto on 2014-05-08
What CPU?

---

### Post by nosto53 on 2014-05-09
OK, I guess I have the same question - and my laptop is a late-2006 Macbook Pro 2,2 . 
Intel Core 2 Duo T7600 (2.33GHz) CPU, 4GB DDR2, 120GB SSD with a new copy of Lion OS(10.7.5).

Dual boot Mac/Ubuntu 14.04 --- Can this really work??

RickO 0110 0010 (age, dummy ;-) )

---

### Post by blgarion on 2014-05-10
Another one with the same issue: Ubuntu 14.04 DVD trying to run over refind. My computer is Macbook 2,1 and once I try to run the DVD from the refind menu it goes to the legacy boot and it only shows two options, letting you only press option 1 or 2. 
It is completely frozen by then.

I guess that is lack of support, I´ve been able to install Ubuntu 12.04 and Elementary OS based on it.

---

### Post by ryan122 on 2014-11-01
I'm guessing the problem with trying to install 14.04 64-bit directly on a MacBook 2,1 (late 2006) is the 32-bit EFI bootloader on these systems.  I tried to install 13.04 from a DVD last year and it wouldn't boot.  Eventually, I found a '12.04 LTS for Mac' iso that would boot.  I have done the following:
1) Installed refind
2) Installed 12.04 (64-bit) LTS
3) Immediately upgraded to 14.04 LTS using the update manager

With exception of the webcam, everything seems to work.  I found the fan running pretty constantly when using the Unity desktop and have additionally installed the Lubuntu desktop for a quieter/cooler experience.

---

### Post by clenny on 2014-11-28
I have a Macbook 2.1 on which I just installed 14.04. I installed the 32 bit since I don't have a lot of RAM on the old Macbook. I had some issues getting the Mac to recognize the DVD I burned so I could install it but I turned on the computer one day and the DVD started right up and I chose install. It worked and seems ok so far although I can't seem to get the TOR browser to work yet.
I'm not sure what help I could offer except to say I managed to install i successfully.

---

### Post by chrb on 2014-12-04
With an old Mac that refuses to boot the 14.04 ISO you can either update the Mac firmware from within OS X, or patch the ISO using the code in [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16)

---

### Post by neil20 on 2014-12-05
Hi All,

I'm looking to put ubuntu (or possibly Xubuntu) on my wife's Macbook 2,1... I bought her a tablet, so she has little use for the Macbook anymore. I thought I might try to breathe a bit more life into the now unsupported, but still fully functioning, system. It's the base CPU for that model, but the ram is upgraded to 4GB (though I think it technically only uses 3GB). 

I'm wanting some guidance on what version of Ubuntu to install, and some basics on how to go about it. I'm not a complete noob to linux, I actually setup and run an ubuntu server on an old HP desktop I have (relying heavily on internet tutorials). I use it as a media centre and to run time machine backups over my home network. With regards to installing Ubuntu on an old mac, I'm a little confused by the whole 32-bit EFI bootloader issue, I don't really understand what it's all about.

Could someone help point me in the right direction, maybe suggesting some guides to read?

[COLOR=#000000]
[/COLOR]

---

### Post by ZackDeLaRocha on 2015-01-07
I recently installed Ubuntu 14.04 on my old macbook 2,1, and everything works better than expected. :)

I downloaded and burned a ubuntu 14.04 (x86) dvd, and followed the "Dual-Boot: Mac OSX and Ubuntu" part of the guide here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

After the first instalation, I tried to "Fix the Partition Tables", but that led me to a dead end where I couldn't boot Ubuntu anymore.
After this, I made a second clean install (where I think I ended up) ignoring the "Fix the Partition Tables" section. And it worked! :)

With my portuguese keyboard I couldn't write an '@' because this keyboard doesn't have a "Alt Gr" key, so I had to remap the key next to the right "cmd" key.
To do that, I created a file in my home dir named *.Xmodmap* with the following content:

```
keycode 104 = ISO_Level3_Shift Multi_key ISO_Level3_Shift Multi_key
```

After this, I created a script named *keymaps.sh*  with the following content, and inserted it in the startup applications:

```
#!/bin/bash
xmodmap ~/.Xmodmap
```

Finally, I installed the iSight firmware as explained [here]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight"), using the firmware available for download [here]("http://turanct.wordpress.com/2010/06/11/use-your-macs-isight-on-ubuntu/#comments").

After this, i have a fully functional system. It still has some hiccups here and there but, as I said before: everything works better than expected. 

Hope this helps! ;)

---

### Post by smnbldwn on 2015-05-29
Hi, I have a Macbook 2,1 with a Portuguese keyboard too. Unfortunately, I jumped into installing Ubuntu 14.04 without checking all the info. I have done this on loads of PCs before in my job, I teach Computing and use Edubuntu at school.
I thought I would revive my old laptop which was running 10.4 and was very out of date. The first couple of times, nothing happened with the install disc but eventually it started and I chose "Erase and install Edubuntu 14.04" I now now that I should have sorted out the boot problem before I started but now its too late. The boot is slow and unreliable and involves lots of white and black screen, sometimes working and sometimes not. When it works, the macbook runs beautifully although it seems the iSight won't work unless I try the trick above. Even the wi-fi works, which is a problem on most of the old windows laptops I have tried with Edubuntu.I tried running Boot-repair but this killed the boot completely and I had to re-install. My Mac boot disc is in another country, does anyone have any ideas? I am very impressed by how well it runs when it works though and I use this OS on all kinds of machines. I used the x86 32bit version BTW.

---

### Post by smnbldwn on 2015-06-05
Is there any way to sort out the boot manager without re-installing Mac OS?

---

### Post by typo-joe on 2015-06-22
I successfully installed Mac OS X 10.6.8 (snow leopard) and Ubuntu 14.04.2-Desktop (32 bit) on a Mac Book Pro 1,1. I didn't have any issues with installation or start up.

I didn't use a disk to install though, I used a bootable USB flash drive... my optical drive doesn't work any more. If you aren't scared of the Terminal, which I doubt you are, you might give installing from a USB drive a shot. You have to use Terminal to convert the downloaded iso file to dmg/img file and then use it to install it as a bootable disk on the usb. Pretty easy stuff.

Before install, I did install rEFIt on the Mac OS, in order for the system to recognize the boot drive of ubuntu.

---

### Post by joshualmartin on 2015-07-30
You need to get the +mac image for which ever release you are trying to install on macbook 2,1 with this problem. I found the article that explains it here:

[https://askubuntu.com/questions/468437/where-can-i-get-a-mac-image-of-ubuntu-14-04-lts/468447#468447](https://askubuntu.com/questions/468437/where-can-i-get-a-mac-image-of-ubuntu-14-04-lts/468447#468447)

I'm currently downloading this release to install on my mid 2007 macbook 2,1 1181 T2700 intel macbook core2duo. Hopefully this will allow me to install 64 bit Ubuntu using the old bios boot loader. I'll confirm back here if it works properly.

EDIT: Confirmed! - The above link is a Ubuntu 14.04 LTS 64-bit which uses the legacy bios boot loader. Downloaded the iso, burned it to a DVD, crossed fingers and it booted into the Live CD! - installing now.

---

### Post by dantheperson on 2015-08-06
Hi,

Where can i find instructions for booting from USB?  I also have a MacBook 1,1 with dead DVD drive.

Thanks,
Dan.

---

### Post by typo-joe on 2015-08-14
> **dantheperson said:**
> Hi,

Where can i find instructions for booting from USB?  I also have a MacBook 1,1 with dead DVD drive.

Thanks,
Dan.


[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

---


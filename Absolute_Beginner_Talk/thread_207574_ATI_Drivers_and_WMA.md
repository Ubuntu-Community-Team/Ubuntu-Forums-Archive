---
title: "ATI Drivers and WMA"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by SizzleBeast on 2006-07-02
Hi all!

I've two questions, first, I looked around on the forums, but, I hadn't been able to find any good help for ATI drivers.  I did notice that there was quite a bit of information for NVIDIA drivers, so I could just as easily be missing something, however, I am very new to Linux and Ubuntu, so I would not likely understand much of what it was talking about. Anyway, I believe I'm having trouble getting Ubuntu to recognize the information about my ATI card.  I'm not 100% sure that information I have about it is correct, but, from what I've seen, it has incorrect information.  It says that have a card from Tungsten Inc.although I know that manufacturer is ATI.  It also says that my card, which is a ATI Radeon 9800 Pro 256 MB, is only a 128 MB graphics card.  First, is there way I can check what it knows?  And is there a better driver or configuration so that Ubuntu can take full advantage of the card?

Secondly, I read through the wiki on Ubuntu site about listening to WMAs on Ubuntu.  Although, I thought I did what it said, it did not end up working.  Can anyone help me or point me in the right direction of how I can get WMA used to work?

Edit: Thinking back, I'm not sure if the information I used was on the ubuntu site.

thanks in advance!

Btw, if you see any spelling errors or weird information, i probably just missed it. I'm trying some voice recognition software. :)

---

### Post by MaximB on 2006-07-02
about the ATI card - I have the very asme model and the guys here managed to help me - there are a LOTS of guids here in the forum about ati cards - you should look for them
about your second question - you need to download codecs - in the add/remove programs enable the restricted programs and download the codecs.

---

### Post by 3rdalbum on 2006-07-02
I'll leave the first problem to someone who knows more about what they're talking about than me, but you'll need to download the latest proprietry ATI drivers for Linux. Don't use the version from the repositories, it's unsafe for your data.

For the second problem, have you tried going to [www.mplayerhq.com](www.mplayerhq.com) and downloading the w32codecs package? Was that the instructions you followed? You'll also need the MPlayer package from the repositories.

---

### Post by catlett on 2006-07-02
I have an ATI Radeon 9600 128mb card. This is what I used to get it working properly
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
``` Just cut and paste those commands one at a time in the terminal. Then reboot.
 If for some reason you have issues after this. Enter this command and it will change everything back after a reboot.
```
sudo cp /etc/X11/xorg.conf_backup  /etc/X11/xorg.conf
```
This is the guide I use when setting up a new install. Just follow it exactly. You can just cut and paste the command sfrom the page into the terminal. YTou don't have to install everything listed, youy can pick and choose if you want. [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by SizzleBeast on 2006-07-02
Thanks fior all the replys.

So far, i've ran all those commands in terminal, and that mostly fixed it, however, it still says it is only a 128 MB graphics card. Secondly, the first reply was talking about a ATI forum on here, but i don't see one, only a video and sound forum, which looked like it had mostly Nvidia information.

I'm off to try the information with the codecs.

Edit: The guide got my codecs working :)

Thanks for all the help :)

---


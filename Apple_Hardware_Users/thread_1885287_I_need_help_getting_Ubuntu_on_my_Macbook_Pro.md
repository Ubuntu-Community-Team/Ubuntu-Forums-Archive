---
title: "I need help getting Ubuntu on my Macbook Pro"
date: 2011-11-22
forum: Apple Hardware Users
---

### Post by Zukaro Travon on 2011-11-22
I'm trying to triboot Windows 7, OS X Lion, and Ubuntu 11.10 on my Macbook Pro (13 inch).

I tried rEFIt and all that did was make OS X unbootable.  Whenever I try to just run Ubuntu from the live CD it says

```
BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system
```I have no clue what the problem is; but this live CD worked on my PC, so I don't think it's the CD.  I have no clue how to fix this, and every guide I find tells me to use rEFIt (and every time I use that, all that happens is OS X becomes unbootable).



I'm very new to Macs and I'm pretty new to Linux (although I do have a tiny bit of experience with Ubuntu).

Any help would be appreciated very much.

---

### Post by davidryderuk on 2011-11-23
Hi,

If you want to use the 64 bit version of Ubuntu then use the '64-bit Mac desktop CD'. The version on Ubuntu's main downloads page can turn your computer into a very expensive paper weight (as in not being able to turn it on at all). --> see launchpad bug #774089

[http://cdimage.ubuntu.com/releases/11.10/release/](http://cdimage.ubuntu.com/releases/11.10/release/)

[http://cdimage.ubuntu.com/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso)

My Macbook won't boot any recent Ubuntu CDs either. I don't think it's an issue with Lion, since I'm running Snow Leopard.

Your problem with refit sounds like a separate issue. I would guess it has something to do with installing refit on the latest version of Lion.

[http://www.google.co.uk/#hl=en&cp=6&gs_id=h&xhr=t&q=refit+lion&pf=p&sclient=psy-ab&biw=1360&bih=571&source=hp&pbx=1&oq=refit+&aq=0&aqi=g4&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=39dafac395169a6a](http://www.google.co.uk/#hl=en&cp=6&gs_id=h&xhr=t&q=refit+lion&pf=p&sclient=psy-ab&biw=1360&bih=571&source=hp&pbx=1&oq=refit+&aq=0&aqi=g4&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=39dafac395169a6a)

Perhaps you could just use the Option key for the time being?[COLOR="Blue"] --> I changed my mind about this, please see post #8 [/COLOR]

[http://support.apple.com/kb/HT1310](http://support.apple.com/kb/HT1310)

---

### Post by Zukaro Travon on 2011-11-23
> **davidryderuk said:**
> Hi,
**[COLOR=Red]If you want to use the 64 bit version of Ubuntu then use the '64-bit Mac desktop CD'[/COLOR]**. The version on Ubuntu's main downloads page can turn your computer into a very expensive paper weight (as in not being able to turn it on at all).

[http://cdimage.ubuntu.com/releases/11.10/release/](http://cdimage.ubuntu.com/releases/11.10/release/)

[http://cdimage.ubuntu.com/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso)

My Macbook won't boot any recent Ubuntu CDs either. I don't think it's an issue with Lion, since I'm running Snow Leopard.

For the moment the following solution works quite well.

[http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/](http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/)

Your problem with refit sounds like a separate issue. I would guess it has something to do with installing refit on the latest version of Lion.

[http://www.google.co.uk/#hl=en&cp=6&gs_id=h&xhr=t&q=refit+lion&pf=p&sclient=psy-ab&biw=1360&bih=571&source=hp&pbx=1&oq=refit+&aq=0&aqi=g4&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=39dafac395169a6a](http://www.google.co.uk/#hl=en&cp=6&gs_id=h&xhr=t&q=refit+lion&pf=p&sclient=psy-ab&biw=1360&bih=571&source=hp&pbx=1&oq=refit+&aq=0&aqi=g4&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=39dafac395169a6a)

Perhaps you could just use the Option key for the time being?

[http://support.apple.com/kb/HT1310](http://support.apple.com/kb/HT1310)


I was using the Ubuntu Mac version (I also tried the normal version).
(should probably mention: my Macbook uses an Intel processor (the Intel i7), so I don't think the Mac version of Ubuntu will work (however I still tried it either way)).


The problem is booting off the live CD currently.  Mainly anyways; I can't get into Ubuntu at all.  I've tried using the option key to get into the live CD but it does the same thing as when I hold C to boot onto the CD.  It displays the logo and such but after it finishes with the logo screen it doesn't do anything (it gives me a terminal basically which tells me it can't find the live filesystem).




Something like that.  I'm going to look at a few of those links you've posted (I think I already saw one which may help me (thanks for the help so far :))).

---

### Post by davidryderuk on 2011-11-24
> I was using the Ubuntu Mac version

Great. I didn't expect this to solve your original problem, I just wanted to be sure you didn't end up having a worse one.

> my Macbook uses an Intel processor (the Intel i7), so I don't think the Mac version of Ubuntu will work

The CD I gave a link to (file ends in 'amd64+mac.iso') should be able to install the 64 bit version of Ubuntu on 64 bit intel processors. I can see the confusion though, since the actual description of the CD doesn't mention intel chips anywhere. The other type of processor you can find in Macs is the PowerPC processor. The term 'PowerPC' is usually mentioned in the downloads page. The PowerPC iso won't work with your computer.

The normal 32 bit version of Ubuntu (file ends in 'i386.iso') should also work fine with your computer. It's just the 64 bit version of Ubuntu on the main downloads page that is a bit risky (file ends in 'amd64.iso').

---

### Post by davidryderuk on 2011-11-24
> It displays the logo and such but after it finishes with the logo screen it doesn't do anything (it gives me a terminal basically which tells me it can't find the live filesystem).

I originally thought that you might have better luck booting from a USB stick, using one of the iso files I suggested in the post above.

However after hearing that you have one of the more recent Macbook Pro's it might be a good idea to check what model laptop you have and find advice tailored to that specific model. If you know when you bought your Macbook Pro you can probably just work out the model number from wikipedia. If you don't know the exact release data for your laptop, the information should be available somewhere in the 'About this Mac' menu item in OS X.

[http://en.wikipedia.org/wiki/MacBook_Pro](http://en.wikipedia.org/wiki/MacBook_Pro)

---

### Post by davidryderuk on 2011-11-24
After trying one of my suggestions, and looking up posts from people with a similar laptop model to you I came across the following thread. 

[https://discussions.apple.com/thread/3511567?start=0&tstart=0](https://discussions.apple.com/thread/3511567?start=0&tstart=0)

The whole thread is worth bookmarking and reading later since 'ds store' is much more familiar with dual booting Lion and Ubuntu than me, and the other user has almost the same hardware and problem as you. I have summarised some comments below, which in retrospect I would agree with:

>  
Booting and installing Ubuntu on a Mac can brick the machine, as the header on the GPT has a partial MBR like Windows full MBR, so it's mistaken for one and attmepts to install............

..........If you had a pre 2011 Mac and no Lion, just Snow Leopard, I would say no problem........

........A much better option for you is to get a inexpensive machine and install Linux on it, or buy one already installed, until this Lion buisness settles down and urber geeks tweek Linux on Mac's again ...........


.......If your going to mess with Linux you should do so on generic PC hardware first, then on a spare older Mac, then on your main newer Mac after you have resintalled OS X a few times so you know how to get your Mac back..........

......... Linux can run on a Mac, it's just the hardest geeky thing to do as a Mac has differences from generic PC's and you need to take in more factors, what Linux requires and so forth to make it all work.
 

I don't have quite the same problem as you since I'm running Snow Leopard on a mid-2010 Apple laptop. However there are still quite a few things to consider, even on my machine (as you can probably see from my previous posts). If you have a PC lying around that works well with Ubuntu then it might just be worth using that computer for the time being.

Note that you can  probably still boot up and install Ubuntu using one of the links I gave earlier. However after thinking about it, and reading the comments from 'ds store' I do not think that would be a good idea.

---

### Post by Zukaro Travon on 2011-11-24
The "ubuntu-11.10-dvd-i386" iso sort of works.  It gives me the option  to install Ubuntu.  Rather then just install it I chose the "try Ubuntu"  option, it still gives me the same problem as on all the other times I  tried with my other CD's.  So I'm not sure if that would happen again if  I installed it (if I do install it, it's going to be along side Windows  7 on BootCamp, so I'm not sure if that'd make a difference or anything  either).

---

### Post by davidryderuk on 2011-11-25
Refit seems to have issues with Lion and the latest version of Linux. 

It is more than a method of choosing a startup disk. 

Without refit your Mac might end up forgetting about the Linux and Windows partition. That is why nearly all the guides recommend installing refit.

Have you considered using Virtualbox instead, or another computer?

[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by Zukaro Travon on 2011-11-25
The only other computer I have is an Acer Aspire One ZG5 (which is currently running Linux, but it's a pretty old computer (so I bought this new computer cuz 1, I wanted to try out a Mac and 2, I needed a new computer anyways)).

And I could use VirtualBox, but I'd rather triboot.

Wouldn't it work if I made my Windows partition using BootCamp then putting Linux in a partition inside BootCamp?  As for it forgetting Windows, that's okay for now as I don't have anything on any OS on there (if I need to reinstall OS X Lion again that's fine too).

(I really only need Windows, but I'd like to have all 3 OS's (I guess I need OS X also since it updates the firmware of the computer (or so I've heard anyways)))

---

### Post by davidryderuk on 2011-11-25
It is a good idea to pre-partition your Mac using Disk Utility or Boot Camp. It is also good if you have anything important on Windows and OS X backed up. 

Another thing you want to check is whether you can reinstall OS X if you accidentally mess up the hard drive. This would mean having some sort of install CD (which OS X doesn't ship with anymore).

A large number of the Apps on Linux are available on Windows, such as Gedit, Banshee, Firefox, Openoffice, Thunderbird, VLC player, Pidgin, Python, Zotero and Geany, 

I think you'd probably find the situation has improved in six months. I just don't think it's a great idea now.

---

### Post by Zukaro Travon on 2011-11-25
k
Well, I'll probably wait then.
As of currently I've got nothing important on OS X or Windows; and I believe I can make an image of OS X with the disk utility (not sure, but I do have a few DVD-R's left).

I've already reinstalled OS X a few times with the recovery hard drive.
(since rEFIt made it unbootable whenever I tried it)




But anyways; I'll probably wait a bit then try again I guess.
And thanks for the help.  :)

---

### Post by davidryderuk on 2011-11-25
Hope you enjoy your computer. I wish mine had a backlit keyboard. :)

When you try doing it again you might want to back up your Recovery HD onto a USB stick (it's nice to have it somewhere Linux can't mess it up):

[http://support.apple.com/kb/DL1433](http://support.apple.com/kb/DL1433)

---

### Post by docbop on 2011-11-25
Why not go virtual instead of multi-boot.  I have OS-X Lion, Win7, Backtrack, Ubuntu all on two of my Macs.   With latest release of Fusion it has the fixes for Lion OS X.    Virtualbox I haven't tried with Lion but it works with Backtrack with USB wifi radios thats that Mac doesn't even support.

I would suggest consider going virtual.

---


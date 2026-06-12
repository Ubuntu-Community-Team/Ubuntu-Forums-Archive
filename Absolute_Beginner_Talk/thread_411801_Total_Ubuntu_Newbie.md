---
title: "Total Ubuntu Newbie"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by SteveTx on 2007-04-17
A very techie friend of mine told me about this site. I just purchased a new laptop that came with Vista and I am beginning to hate microsoft in the worst way. I am in Real Estate and have to use internet explorer on several of my real estate online software programs.  I have several macs and several older pcs and have downloaded the Ubunto iso to my mac and burned a copy for my older pc's to try to get started. I eventually would like to get rid of Vista on my laptop and go 100% with Ubuntu if there is a Internet Explorer browser compatible with Ubuntu. I use Firefox for several apps, but I still need ie on several occassions. My first dilemma is how to install the Ubuntu onto an older 32 bit pII currently using win98. I have 4 other pc's with XP on them and would like to switch all my machines to Linux.
Is there a 1,2,3 system for loading? I've tried putting the Cd in and rebooting, but it just loads win98. Do you install from dos?

Please help.

Thanks:confused:

---

### Post by Jagot on 2007-04-17
You will need to ensure your BIOS is set to allow the system to boot from the CD drive.

---

### Post by freebird54 on 2007-04-17
Just to answer the last question first, you have to set the BIOS up to load from the CD - if it can!  When you boot up, there is usually a message such as 'Press DEL to enter setup'  (or maybe F10 or F12).  Once into setup (in the BIOS) there is an option to set the boot order, put the CD first.

*IF* however, the choices for boot order are A,C or C,A things get a little trickier - you might want to try one of the XP capable machines first!

---

### Post by Jagot on 2007-04-17
You may also wan to have a look at these sites:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

They procide some guides to get you going with installing, and some other useful stuff.

---

### Post by tommcd on 2007-04-17
To boot from the CD you have to set the computer's bios to set the first boot device to cdrom. Consult your PC's manual of manufacturer's website in how to do this. Usually you hie DEL, or F2, or possibly some other key right after you hit the start button, and before windows loads, to get into the bios. Once there, select boot options, then change to cdrom as 1st boot device. Hit F10 to save and exit.
Also, did you burn the CD as an iso file? You can't just copy it to a CD. See this:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
After you boot ubuntu, try out the live CD first. That way you can try it without actually installing it. Then if you like it, install it on one your older PCs first to get some experience with it. See this site for good installation info:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
Just work your way down the menu on the left of the page. Good luck, and welcome to the forums!

---

### Post by bmagyarkuti on 2007-04-17
Microsoft only creates software for Windows and Mac OS, so there is no Linux (Ubuntu) version of Internet Explorer.

Yet, it is relatively easy to set up Microsoft Internet Explorer 6.0  on a Linux machine, using the Wine emulator.

---

### Post by hyper_ch on 2007-04-17
Actually you can install MSIE on Ubuntu.

I haven't tried it but here's a howto: [http://www.howtoforge.com/ubuntu_internet_explorer](http://www.howtoforge.com/ubuntu_internet_explorer)

Furthermore if you bought a new computer you could also make virtualization. This means that you can start Ubuntu and when it's started you could also load another OS within Ubuntu... of course this uses quite some system ressources but I have setup WinXP that way for a few things that only work in Windows. That way you could also run a "save" Windows at the same time you run Ubuntu :)

---

### Post by camz on 2007-04-17
I know that somewhere on psychocats there is a guide to installing IE

---

### Post by insane_alien on 2007-04-17
would the IE tab extension for firefox work? i don't know if it works on ubuntu but its worth a shot.

---

### Post by n3tfury on 2007-04-17
> **insane_alien said:**
> would the IE tab extension for firefox work? i don't know if it works on ubuntu but its worth a shot.

that won't work by itself.  IE still needs to be installed.

---

### Post by silverglade00 on 2007-04-17
Just in case you eventually decide to dual-boot that Vista machine, here's my HOW-TO:

When Microsoft released Vista, they also released a problem for users wishing to dual-boot with Linux. They updated NTFS and made it slightly incompatible with the previous version, which makes you, the new Ubuntu user, have to jump through an extra hoop to get your Linux on.

This HOWTO is for the person who bought a computer with Vista pre-installed. This means that you will have the entire drive taken up with probably 2 partitions: the main Vista partition and a recovery partition. The recovery partition can be quite large. Mine was over 2.5GB. That is some room that I wanted back, so I ordered the recovery DVD from my vendor. It made me mad because that should be in the box, but I did it anyway. The point is, do something to make sure you can get your Vista back in the event that 1) it gets hosed and 2) you actually want it back.

STEP 1: Testing your computer

The very first thing you should do is run the LiveCD to be aware of any potential problems. Make sure that you have at least one working Internet connection before doing anything. You will want it to update your system and install other software. You will really, REALLY want it if you need to look up how to get troublesome hardware running. In general, if it works from the CD, it will work from the installed system. Now, you will probably be tempted to click that shiny Install button. Resist. Seriously. You will click it later.

STEP 2: Reboot into Windows

I know, I know, it sounds crazy. Hopefully, this will be a rare event in the very near future. Go make a sandwich, Vista takes a while to start up. Right-click on Computer (it's not MY computer anymore, it's Microsoft's) and choose Manage. Give yourself permission to choose Manage on the popup.

Step 3: Knock Vista down to size

You are now in the Computer Management (CM) window. Well, you have it open anyway, but I guess you are in this window since you are reading it. In the CM window, on the left side, click the little triangle next to Storage to show Disk Management. Click that once to fire it up. When it loads up, you will see a listing of your partitions and a bar graph at the bottom representing those partitions. In the bar graph, right-click the one marked Vista (probably C: ). Choose Shrink Volume...

This part is a little tricky. You have one box that you can type in. In that box, type the number of MB (not GB but MB) that you want to allocate for ALL of your Linux partitions combined. Type in the number and slap the Shrink button. Go wash the car or take your dog for a walk. This will take a while.

STEP 4: Gimme my Ubuntu!!

Ahh, you are back. Hopefully, Vista is done shrinking itself. At this point, you can put the Ubuntu LiveCD back into the drive and reboot. Now you can click that shiny, enticing Install button. Tell the Ubuntu installer that you want it to use the free space on the drive and let it do its thing. In about 15 minutes, you will have a beautiful Ubuntu installation dual-booting with your Vista install. Each time you reboot, you can choose which system you want to use. Enjoy your system, and try not to neglect your Vista install too much. You may not want to use it, but it is pretty high maintenance. ;)

---

### Post by jvc26 on 2007-04-17
Another +1 for the psychocats installation instructions - the menu on the left of the site pretty much works you through the whole process from downloading the iso to installing it or dual booting. Good luck :)
Il

---

### Post by darkrose on 2007-04-17
On the Internet Explorer subject, have a look at the [IEs4Linux](http://www.tatanka.com.br/ies4linux/page/Main_Page) site, there's a handy little script there for easily installing IE 5/5.5/6.

---


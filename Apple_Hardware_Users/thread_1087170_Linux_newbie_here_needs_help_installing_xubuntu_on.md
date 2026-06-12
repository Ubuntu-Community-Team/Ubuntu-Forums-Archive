---
title: "Linux newbie here needs help installing xubuntu on iBook G4!"
date: 2009-03-04
forum: Apple Hardware Users
---

### Post by NovaFlame on 2009-03-04
Hi, I am really new to linux and I am looking to put xubuntu on this old late 2004 model iBook. 

My specs are: 

iBook G4 1.2ghz
512mb of RAM
ATI Mobility Radeon 9200 32mb VRAM 

I know this could probably run Ubuntu fine, but I want a lightweight OS, so xubuntu is the way to go for me. 

Couple questions first. 

1. Where do I get the xubuntu PPC packages from? 
2. Can I install xubuntu on my external hard drive? Its formatted in HFS+ but I suppose I can reformat it if need be as well. My internal hard drive is only 30 gb and I really would rather not partitioning it. I want to keep Mac OS X 10.4 on my internal, well having xubuntu on my external. 

And my most important question of all is... 

**Can I please have a step by step easy guide to installing this on a iBook G4** 

Thanks :)!

---

### Post by conal on 2009-03-07
Hi NovaFlame

I think what you want to do will be very difficult, I wanted to do much the same with an iMac G4. There are instructions for installing ubuntu to an external HD with a ppc mac on the web (can't remember where, you'll have to google a bit), but they are very complicated and apparently it only works with Hard drives that connect with a firewire, not ones that connect by USB (as mine does).

In the end I decided I had to dual boot from the main hard drive. This meant wiping the hard drive, installing OS X first, (using the OS X installer to partition the Hard drive), Installing OS X on the first partition, then installing Ubuntu on the other partition using the Ubuntu live cd. I couldn't find a recent Xubuntu live cd so I installed the Ubuntu Hardy Heron one (from [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)) 

Once ubuntu was installed I used the synaptic package manager to install the Xubuntu-desktop package, then logged out changed, my session to xfce, and made that my default.

I used the hardy live/desktop cd because I feel safer with the graphical interface and because it was the most recent version of Ubuntu offered as a live cd for ppc. However if you really want to start with Xubuntu there are alternate install cd's of intrepid ibex available here: [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

I realise this  doesn't help you do what you want to do, however I ended up tearing my hair out trying to do what you want to do, so I hope this might save you some agro!

thanks

Conal

---

### Post by tiresia on 2009-03-07
Running and installing GNU/Linux on an external USB Drive is not difficult, it's slow.

There are many ways to install Xubuntu. The easiest, that most people ignore, is to download the Xubuntu Intrepid Installer from the torrent server (be patient, it can last a bit) [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

First of all: if it is your first install, BACKUP IMPORTANT DATA!!!
After downloading the CD image, burn it with the Apple Disk Utility at low speed. Start from the CD pressing the C-Key
If you want, you can try to install Xubuntu on you external HD, just to get an idea how it can work. Choose it when the partitioner ask you how you want to install (use the entire HD). Be sure to choose the right HD!!!

When you are finished, reboot and at start up, press the OPT-Key. You should be able to see your new installed Linux. 
If you have problems with the video, restart and at the Yaboot (the Powerpc Bootloader) prompt, type: ```
Linux video=ofonly nosplash
```

If you find, as I believe, that it is too slow, you should follow what conal suggests you, partitioning the HD. You don't need to reinstall macOSX. You should resize the partition where MacOSX is using the Installer. 

Let us know, how it works for you, and if have still questions.

---

### Post by conal on 2009-03-07
Thanks tiresia, I stand corrected!

---

### Post by mkvnmtr on 2009-03-08
If you are looking for fast I don't find Xubuntu faster than Ubuntu. You might think about a minimal install and using xfce4 for the desktop. It is a good bit faster than the full Xubuntu install and has lots of goodies you can install.

---

### Post by anarchoprole on 2009-09-28
Hi,

 I'm also a mac user who has a imac g4 I would also like to install ubuntu and enter the linx world (also resurrect my favourite machine) but I'm having a problem at the first hurdle.

[QUOTE=conal;6853688]

"This meant wiping the hard drive, installing OS X first, (using the OS X installer to partition the Hard drive)"


I don't see this option to partition when i try to erase and install, when does it pop up? I'm using osx 10.2 if that's relevant. Is there any way of just installing ubuntu without having to partition and having no osx on at all or is that out of the question

T.I.A.
Ferdi

---


---
title: "making copies of encrypted DVDs"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by nickle on 2006-04-01
My kids are continually asking me howto copy DVDs they borrow from school mates.
Can somebody tell be the best way to do it? I live in a country where this activity is (still) perfectly legal.....

---

### Post by taurus on 2006-04-01
I think you are look for dvdrip or xdvdshrink which is a Linux version of dvdshrink for Windows...

---

### Post by nickle on 2006-04-01
I cant find xdvdshrink in synaptic. I have looked at dvdrip, but I am too dumb to figure it out. I am really not well up on the formats it offers mpeg/xdvi etc. Is it not possible to simply make a one on one copy? If not can the copied DVDs be played on my DVD player like normal DVDs?

---

### Post by ronmarley1 on 2006-04-01
[QUOTE=nickle]My kids are continually asking me howto copy DVDs they borrow from school mates.
Can somebody tell be the best way to do it? I live in a country where this activity is (still) perfectly legal.....[/QUOTE]
I like K3b.  It's a KDE app., but runs fine in Gnome.  It's available for download in the repos.  It runs on top of cdrdao, so if you have not installed that, you will need to add that also.

---

### Post by nickle on 2006-04-01
I dont think K3B will copy encrypted DVDs????

---

### Post by ronmarley1 on 2006-04-02
[QUOTE=nickle]I dont think K3B will copy encrypted DVDs????[/QUOTE]
OOPS!  Sorry about that...  I thought I read CDs.  DOH!

---

### Post by Oz_hack on 2006-04-02
Try K9copy its a really good app and will copy dvds its in the repros

---

### Post by patrick295767 on 2006-04-02
DVD ripping and DVDshrink ... 
===========
I would recommand you : dvdshrink windows or xdvdshrink
==========

Quote:
This is very helpfull to backup you cd and dvd into iso images:

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

To make an ISO from files on your hard drive, create a directory which holds the files you want. Then use the mkisofs command.

mkisofs -o /tmp/cd.iso /tmp/directory/

This results in a file called cd.iso in folder /tmp which contains all the files and directories in /tmp/directory/.

For more info, see the man pages for mkisofs, losetup, and dd, or see the CD-Writing-HOWTO at [http://www.tldp.org](http://www.tldp.org).

Hope it helps
Sniff.


DVD ripping, Programs:
================
dvd::rip dvdrip
[http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

Acidrip

sudo apt-get install thoggen
[http://thoggen.net/](http://thoggen.net/)
Screenshots: [http://thoggen.net/screenshots/](http://thoggen.net/screenshots/)

In another thread someone raved about tovid. The website
[http://tovid.berlios.de/en/index.html](http://tovid.berlios.de/en/index.html)

maybe k3b for ripping ??
=========
Video convertions:
[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)


DVD double layers to DVD mono layers: wine & dvdshrink
============
wine & dvd shrink:
How to:
[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

speed windows eg: 13,000 kbs
speed into linux 10,000 kbs
abnormal speed in linux : 4,400 kbs
Quote:
If you already have it installed, hit alt-f2 and run the command 'winecfg'. This will bring up the new winecfg panel.

In the applications tab click on 'add appplication' and navigate your way to the dvdshrink .exe. Then set the windows version to 'windows xp' for dvdshrink.
Click on the drives tab and let it autodetect your drives.
Close winecfg and start dvdshrink again and the ASPI error should be gone.

The other problem you're going to have is a that the compression rates won't work properly when you open a disc for analysis. What I am doing at the moment is copying the whole dvd to the hardrive using dvdbackup. It's a command line program but works really well. Once installed you can use this command to backup the whole disc to your home directory

dvdbackup -i /dev/dvd -o /home/yourusername/ -M

I then choose 'open files' in dvd shrink and it is able to analyse the files from the hard disc (created by devbackup) properly and backup in the usual way. I usually backup to an iso image then burn with nautilus or k3b.
by manicka

Quote:
> HOW-TO: Install DVD Shrink with Wine in Breezy

This how-to will install DVD shrink with the new beta version of wine (0.9) from WineHQ. The version of Wine that comes with breezy will install DVD Shrink but will not analyse your original dvd's properly. As always check the relevant copyright laws for your country re backup of DVD's.

I'm assuming that you already have libdvdcss2 installed so that you can play your retail dvd's. If not follow the how-to here

PLF
[edit]
Installing Wine

The new Beta (0.9) release is now valiable at WineHQ and fixes a major bug with the preview window in DVD Shrink. Please use the WineHQ deb in preference to the version that comes with breezy -

Run

sudo gedit /etc/apt/sources.list


add these two lines two your souces.list

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/


now update and install wine

sudo apt-get update
sudo apt-get install wine

[edit]
Configuring Wine

alt-f2
winecfg

This will setup your wine directories in ~/ and start the winecfg control panel

Once the winecfg control panel starts, go to the 'Drives' tab and allow it to autodetect your drive setup, by clicking on the 'Auto Detect' button. Close winecfg

N.B. some users have found that DVD Shrink is not detecting their drives properly. This advice from fergus may help:

By default, when you add a drive to wine it thinks its a hard drive and not a cd-rom. Try going into winecfg and to the devices tab. Then enable the Advanced options and select your dvd drive. It might be listed as a hard drive, change that to cd-rom and then DVD Shrink should pick it up.

Further advice.

Recently I did a fresk wine install by deleting my wine directory and then recreating my wine directory and installing dvd shrink again. I to ran into the 'drive not being detected' problem. A solution which worked was to download and install the latest version of winetools and use this to setup my basic wine configuration instead (after installation use the command '/usr/local/winetools/wt0.9jo' instead of 'wt' to start winetools). I would suggest using Winetools to create the fake windows directory, install arial font, install dcom98.exe and Microsoft Foundation Classes 4x. Winetools will also install IE6sp1 but I would not recommend installing this piece of junk.

IE6 will also mess up the way that dvd shrink runs (surrounding screen turns black) if ie6 is installed as well, so do yourself a favour and give it a miss. Once you have created a base setup using Winetools, you should be able to install dvdshrink as per the rest of this how-to.... enjoy
[edit]
Installing DVD Shrink

Download the DVD Shrink installer. The current version is 3.2.015 and you'll need to do a Google search (try DVD Shrink download) to find it, as the main site no longer carries links to the installer.

In a terminal in the directory that you downloaded DVd Shrink to, run the command

wine dvdshrink32setup.exe

(or whatever the exe file is called)

Follow the installer instructions to install. At the end of the installation uncheck the box that asks to run DVD Shrink now.

when the installer is finished run

alt-f2
winecfg

This will start the winecfg panel again as we have to configure it to run DVD Shrink properly

In the Applications tab window click on 'Add application'

Navigate your way into Program Files-->DVD Shrink and find 'DVD Shrink 32.exe'

highlight this file and click on the open button.

This will now take you back to the Applications Tab window and DVD Shrink should appear in the list in that window.

Highlight DVD Shrink then go down to the Windows Version box and choose 'Windows XP' from the drop down menu.

Click on the 'Apply' button then OK to exit winecfg.


[edit]
Starting and Using DVD Shrink

The installer should have created an icon on your desktop. You can use this to start DVD Shrink or type the following command in a terminal

wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

You can also use this command to make an entry in the Gnome menus with Smeg


Enjoy!


I would recommand also to :
do :
xterm
winecfg
then, do a AUTODETECT for cdroms and so on, once you have added
"C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"
in order to get and make available the DVD drive

---

### Post by Xiunix on 2006-04-03
I find the easiest way is to take the Windows version of DVD-Cloner III via Wine. It's a simple one-click program that does a pure copyt without worrying about the dammed encryptions. "...Google..." the program to find it...

---

### Post by nickle on 2006-04-03
oooh-aaaah now there is a mine of information... thanks to you all. I will try some this stuf out and get back to you....

---

### Post by nickle on 2006-04-04
Thanks guys

K9copy seems to do the job... it's a great tool.

---

### Post by arch stanton on 2006-04-05
I'd like to put in a vote for xdvdshrink. once you set it up it will rip,shrink,and burn with one  click, and clean up all the files when it's done. I'd been using dvd backup and dvdshrink through wine, and then burning with k3b ..xdvdshrink makes copying a breeze .. my 2 cents

---

### Post by sinfreealex on 2006-04-19
Seems that the download links for xdvdshrink are down.  As far as I can tell, it's the only part of Sourceforge.net that is currently down.  I wonder if this is related to the crackdown by Macrovision, as of late, to kill these types of projects (see: DVD Decrypter for Win).

I will second the vote for K9 Copy.  Great to have an all-in-one program.

I am currently moving all my pictures, vids and music to Linux so that I can reclaime the harddrive space wasted by a Win32 install.

---

### Post by lime4x4 on 2006-06-18
when i run this command nothing happens
dvdbackup -i /dev/dvd -o /home/yourusername/ -M

And i have dvdbackup installed

---

### Post by lime4x4 on 2006-06-18
this is the error i'm getting

john@ubuntu:~$ dvdbackup -i /dev/hda -o /home/john/ -M
dvdbackup: symbol lookup error: dvdbackup: undefined symbol: UDFFindFile
john@ubuntu:~$

Oh and hda is my dvd drive ubuntu calls both my dvd burner hda and hdb

---

### Post by vayde on 2006-06-22
Im kind of a stone axe kind of guy, so I use the following:

vobcopy -m (which rips the entire dvd)

mkisofs -dvd-video -o <filename>.iso /path/to/DVD /Directory /created /by /vobcopy/

then burn the resulting .iso with whatever (I use gnomebaker)

---

### Post by Blissfull on 2006-07-04
Not to be a killjoy, but I must remind you that copying a DVD you do not own (Loaned DVDs) is Illegal in most countries unless the copyright on the DVD explicitly allows it (Creative Commons and Public Domain contents). In some countries even lending a DVD for a friend to watch is illegal. And in some countries making backup copies of DVDs you own is illegal as well.

Your public anoucement ends here.

P.s. Before I start a flamewar... there is something you can do about this if you want to help "shape a new future". Try to buy/get Creative Commons content over copyrighted content. It's legal and helps send a message.

---

### Post by Hi_Im_Fubar on 2006-07-04
[QUOTE=Blissfull]Not to be a killjoy, but I must remind you that copying a DVD you do not own (Loaned DVDs) is Illegal in most countries unless the copyright on the DVD explicitly allows it (Creative Commons and Public Domain contents). In some countries even lending a DVD for a friend to watch is illegal. And in some countries making backup copies of DVDs you own is illegal as well.

Your public anoucement ends here.

P.s. Before I start a flamewar... there is something you can do about this if you want to help "shape a new future". Try to buy/get Creative Commons content over copyrighted content. It's legal and helps send a message.[/QUOTE]

[QUOTE=nickle]I live in a country where this activity is (still) perfectly legal.....[/QUOTE]

I know I'm pretty new and all but I think you should read someone's post before you make a comment...

---

### Post by T700 on 2006-07-04
[quote=Hi_Im_Fubar]I know I'm pretty new and all but I think you should read someone's post before you make a comment...[/quote]

It didn't strike me that the remarks were intended directly for the OP.  Regardless, the idea of supporting GPL/open source items is certainly valid.

Paul

---

### Post by Thundercat on 2006-07-05
Out of interest, what is this country where there is no copyright law?

---

### Post by dimatrod on 2006-08-07
I don't know where he lives in, but in Costa Rica (my country) we have almost no copyright laws and it's so minor that there's stores that sell chip'd Xboxes/PS2s and only copied games are sold.  Also a cop could go in my house charging me for having a hell lot of burned stuff (this doesn't mean I have though) and I could just tell him I have nothing and he'll leave.  Costa Rica laws are that forgiving (I love my country!).

---

### Post by OU812 on 2006-08-07
If you run gnome, I would suggest dvd95. All dependencies are included, so nothing extra to install. However, it is an .rpm file so you will have to install alien; however, that's not a bad thing.

If you run kubuntu, I would recommend k9copy. The dependencies are in the repo (vamps and dvdauthor). But you should install k9copy from source if you want the newer version.

If you run xubuntu, I would recommend lxdvdrip since the dependencies (or most of them) are in the repo. It is easy to use - just pop in a cd and from a terminal enter "lxdvdrip" - and that's it. A config file does all of the dirty work for you.

john

EDIT
xdvdshrink looks like a fine program, but I haven't had a chance to use it yet - ubunutu is the first os I've been able to successfully install it on (zenwalk and vector - both slackware based - had some difficulties). I like the fact that it can copy multiple episodes.

---

### Post by zxee on 2006-08-08
> **vayde said:**
> Im kind of a stone axe kind of guy, so I use the following:

vobcopy -m (which rips the entire dvd)

mkisofs -dvd-video -o <filename>.iso /path/to/DVD /Directory /created /by /vobcopy/

then burn the resulting .iso with whatever (I use gnomebaker)

I like your stone age ideas, however the resulting iso is too big to burn.:-o

Added later: I also tried xdvdshrink as was mentioned in this thread. It appears to be broken in dapper. There is a link for getting it working in breezy here: [http://doc.gwos.org/index.php/Xdvdshrink](http://doc.gwos.org/index.php/Xdvdshrink)

---

### Post by unforeseen on 2006-11-05
I love the ideas posted here but has anyone ever used AnyDVD with DVDshrink via wine?  It's not a free program but if you have the last version you can make backup's of all your movies you own (just in case they become damaged)  The only "problem" is that in windows, AnyDVD sits in the background with DVDshrink is running.  Does anyone know how to open a program and then open a second in wine?

---

### Post by hasimir44 on 2007-06-02
I used to use AnyDVD with CloneDVD2 in windows - worked great.. so I installed vmware server to run these inside of a guest xp inside of ubuntu - works great, but is really slow (maybe because of the networked smb drives I'm writing to?)

so..

I installed dvdshrink via automatix2 (super easy install) and it also worked great (and faster) - however, dvdshrink doesn't provide options for copying the dvd menus, which kind of sucks.. 

so..

I installed k9copy via apt-get and it's perfect (fast with menus) :D

> Does anyone know how to open a program and then open a second in wine?
I installed AnyDVD and CloneDVD2 via wine and I believe AnyDVD was working for wine apps even though I had no indication that it was running in the background.. I just started it like this:

```
wine anydvd.exe
```

then started CloneDVD2: 

```
wine clonedvd2.exe
```

It seemed to work because CloneDVD2 could read a dvd that it would have normally complained about without AnyDVD (CloneDVD2 had a dll problem though - so I ended up using k9copy)

hope this helps..

---


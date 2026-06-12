---
title: "Adding just one file to my PocketPC pda"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-02-25
Hello,
I've given up trying to sync my PIM (contacts, tasks, calendar, notes, etc) between my Ubuntu PC and my PocketPC.  

But I still would like to use my PocketPC pda to play some of my mp3 files. Is there a quick way to copy a file into my PocketPC? Thank you! Thank you. Thank you!


NOTE: I do **NOT** need to sync my data. I just want to add one mp3 file to my PocketPC.

---

### Post by Jucato on 2006-02-25
I found a synce tutorial somewhere around here, in the HOWTO's section. I presume you're using GNOME? I think in that HOWTO, there was a link for a sort of system-tray plugin that will let you browse the directory of your PocketPC. from there I think you can just copy-paste stuff. I'm using KDE and a Windows Smartphone (HTC Tanager/QTek 7070) so I'm not really sure on how things are done in GNOME. but that guide was written for GNOME specifically.

---

### Post by Trab on 2006-02-25
alright, u have 2 options...
syncing PIM data probably can be done, i just never bothered to do it...
so yes, u can move files to ur PDA (pocketpc right?)
either via Synce (ill help you more later if u pick this option)
or via the much better/faster/safer option of using a memory card and a card reader... ive done both, and the second one is better...
if thats not an option (cause you wont/cant spend the money on it) ill help u with synce...

---

### Post by hanzj on 2006-02-25
Trab, my pocket pc pda has a memory card slot, but
1. I don't use any memory cards with it. I only use the main memory on the pda itself
2. I don't have any card readers.

---

### Post by Trab on 2006-02-25
alright, well if ur into mobile media, i would suggest a larger memory card for it... i am able to take all the music i want, plus movies and more with it...
the card reader makes transfers faster, and when u use the Synce Gnome-VFS system, u have to be careful, its tweak my memory card so much... (ive had to reformat it a couple of times just because of that... would hate to think about it doing that to your entire PPC....)

anyways, lemme know wat u wanna do...

---

### Post by hanzj on 2006-02-26
Trab,
Have no plans of buying a media card, a media reader, nor any thing for my pocketpc.  I just want to add/copy one mp3 audio file into my pocketpc from my ubuntu computer. 

What should I do?

---

### Post by hanzj on 2006-03-03
I heard that, using the commandline, we can add files to pocketpc with pcp (librapi2). Can anyone confirm? IF this is the case, please advise.

---

### Post by graham-cracker on 2007-03-06
You can use 'synce-pcp' found in (librapi2-tools). I'm using a Ipaq 1940 and had to do the following before copying the file:

sudo synce-serial-config /dev/ttyUSB0
dccm
sudo synce-serial-start

after this you should be able to use synce-pcp

For a list of other commands you can use to manage files on the pocketpc type in:

dpkg -L librapi2-tools

---

### Post by andreh on 2007-03-24
**It's a Windows Mobile 5 device. See [www.synce.org](www.synce.org).** Maart 2007
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)


> [http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
MultiSync is a free modular program to synchronize calendars, addressbooks and other PIM data between programs on your computer and other computers, mobile devices, PDAs or cell phones. MultiSync works on any Gnome platform, such as Linux.

Currently MultiSync has plugins for
Ximian Evolution synchronization, supporting calendar, ToDos and contacts. Multisync also support Evolution 2 
IrMC Mobile Client synchronization (supported by e.g. SonyEricsson T68i/T610/Z600, Siemens S55 phones etc.) via Bluetooth or IR on Linux, or cable connection. [b]
[Windows CE / Pocket PC synchronization](http://www.microsoft.com/windowsmobile/pocketpc/default.mspx). This plugin is part of the SynCE project, and can be downloaded there. 
Opie and Zaurus synchronization. [/b]
SyncML support (supported by e.g. SonyEricsson P800/P900 and many other phones and devices, for example the SyncML server Sync4j). SyncML also allows you to do remote connection of two MultiSync programs via an encrypted connection over the net. 
Palm synchronization. 
LDAP synchronization. 
Backup of your PIM data.
[http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
> [http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
**Attention Windows Mobile 2005 device owners!**

These devices do not work with SynCE. If you are interested in getting these 
[devices supported by SynCE, please join the SynCE-WindowsMobile5 mailing list](http://sourceforge.net/mailarchive/forum.php?forum=synce-windowsmobile5). Se also bug report 1332550.
[http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
> **It's a Windows Mobile 5 device. See [www.synce.org](www.synce.org).** Maart 2007
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)
> **It's a Windows Mobile 5 device. See [www.synce.org](www.synce.org).** Maart 2007
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)


 

First you must find out what version of Windows your device is running, and visit the corresponding section below: 
For help on finding out what version of Windows your device is running, visit the Discovering your Device's Windows Version page. 
[i]Windows Mobile 2005 
**Windows Mobile 2005 support in SynCE is under development. **
For support and Installation Guides, visit the Windows Mobile 2005 Support page[/i]
[http://www.synce.org/index.php/Installation_Guides](http://www.synce.org/index.php/Installation_Guides)
> [b]STAP 1 
building SynCE with WM5 support from SVN[/b]
Install libsync, librapi2, odccm, synce-gnome 
[http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_Subversion)

[b]STAP 2
subversion of usb-rndis-lite and compiled[/b]
[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite))

[b]STAP 3
Starting A Connection[/b]
"sudo odccm" and then "cd synce-gnome/src" and then "python test.py"
[http://www.synce.org/index.php/Starting_A_Connection](http://www.synce.org/index.php/Starting_A_Connection)
> [http://synce.sourceforge.net/synce/qa.php](http://synce.sourceforge.net/synce/qa.php)

[b]
            Unable to initialize RAPI / Failed to get connection info

Q: I setup everything and connected my PDA but when I try the tools I get a message similar to this in SynCE 0.8 or later:


    *pstatus: Unable to initialize RAPI: An unspecified failure has occurred* [/b] 

Or this message in earlier versions of SynCE:
           [i]ReadConfigFile: stat: No such file or directory
               pstatus: Unable to initialize RAPI: Failure [/i]

If I add -d 4 as parameters to pstatus, I get this a message like this too:
[i]      [synce_info_new:31] unable to open file: /home/david/.synce/active_connection
         [rapi_context_connect:88] Failed to get connection info
[/i]

**A: This means that the PDA has not connected to dccm or that you run the tools and dccm as different users. **Please make sure that:
    1. you are not using an external USB hub
    2. you have installed the patch for the "we're stuffed" bug
    3. you supplied a password to dccm if your device is password-protected
    4. dccm was started before you ran synce-serial-start
    5. that the PPP connection is successful (look in your system logs)
    6. no firewall configuration prevents the PDA from connecting to dccm
    7. you run dccm and the tools as the same user


See * [connect](http://synce.sourceforge.net/synce/start.php) * for more information.
[http://synce.sourceforge.net/synce/qa.php](http://synce.sourceforge.net/synce/qa.php)

---


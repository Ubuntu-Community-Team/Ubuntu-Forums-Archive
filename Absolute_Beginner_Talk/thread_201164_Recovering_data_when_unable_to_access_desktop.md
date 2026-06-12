---
title: "Recovering data when unable to access desktop"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Michael Pollock on 2006-06-21
Though familiar enough with MS Windows to have recovered OS crashes on my own more than once, I have "multiple" issues with Ubuntu. However, I am too new to Linux in general and it in particular to know: 1)how closely these issues may be inter-related; 2)how much of the problem is software and how much hardware; 3)whether one issue must be addressed before any other; and 4)whether I should seek help on this forum, or on the Kubuntu forum given that my problems were the direct result of attempting to switch to it.

If I must give priority to any one issue, it would be how to recover about 200 edited image files & some e-mails in Thunderbird on a drive on which I cannot access the Ubuntu desktop. These may be two separate issues as I was never able to identify/locate a file containing these e-mails to determine what changes might need to be made to the headers to allow me either to export the messages to another program while keeping the original time-stamp intact, or import the messages archived in my current program into it-"resending" messages to myself from the program I want to abandon and "rereceiving" them in the program I will keep would modify the original time stamp and identity of the original sender if not myself

I believe I installed Ubuntu Breezy Badger, but finding the use of version names rather than version #s in Linux confusing, I am not certain what version of Kubuntu I was trying to install. For that reason I suspect I should "recover" Ubuntu rather than Kubuntu. I also suspect that it would be necessary to recover the desktop before it would be possible to recover the files, particularly since I had yet to determine how to install a zip drive (my USB memory card reader might be better option if I could figure out not just where the files I want to copy are located, but how to move them to the memory card) that could give me the option of moving the files to another drive I could access on another computer before fully recovering the OS, though I would still need to determine the proper "context" to use.

I mentioned earlier there may be hardware issues. Installing Ubuntu in the first place was rather involved due specifically to the system board I am using-an ASUS P5GD1-VM. Though it has 2 IDE channels, it only supports 2 IDE drives which must both be on the primary IDE channel, when there are not SATA drives also present, something that is not acknowledged in the user manual, something I discovered as I wanted to set up an IDE slave drive with Windows98 on it, figuring it would be easier to integrate the data files on it into, if not export them to, the Ubuntu drive as most are in formats not needing a Windows98 enviroment to use. No settingss in the BIOS or hardware configuration would eliminate a "cannot find CD" error when I attempted to install Ubuntu until I elmiinated the second IDE hard drive and set the IDE CD drive as slave on the same channedl as the hard drive.

As noted earlier, my problems resulted in an attempt to switch from the GNOME desktop of Ubuntu to the KDE interface of Kubuntu. I made several attempts to download and install Kubuntu, as well as Opera, but the best I was able to do was install some KDE games (which I would have preferred not to install since I am unlikely to play them) and a drawing program. Since the KDE interface is a better "fit" for my "style", I kept trying to install its desktop, but utlimately managed not only to fail in the same, but also "locked" myself out of the Ubuntu desktop. I got numerous reports of errors, too many to consider listing, beginning with "file system seems to be mounted read only". I ended up at a command line prompt, but I was unable to determine what command options were available to me (the list command would not work), much less which, if any, might resolve the problem(s).

As I was afraid of overwriting the data files on this drive if I attempted to reinstall Ubuntu, I tried several "work arounds" to correct this problem, all involving configuring this drive as a slave to a new master. While I was able to get to a desktop using Xandros Linux and have Xandros see the slave drive, it reported only an empty partition on the same about the size of the free space on the drive. With Ubuntu on the "new" master drive, the original master now set as a slave does not appear in any list of installed devices.

It appears that there would be at least 2, possibly 3, options for recovering my data, one being to recover the desktop on the original Ubuntu drive, second being to configure the second Ubuntu drive so that it mounts/sees and can access files on a slave drive, and third being to have someone else do a physical recovery on another Ubuntu system. My only preference between them would be the one that would be the least "convoluted", probably #2 as I could then copying these files to a 

On my last "issue", I found none of the search criteria I used discriminating enough to purge threads that contained search terms I used but did not even come close to addressing the problem(s) I want to resolve. No doubt a part of the problem is that it can be quite difficult, particularly for newbies, to give a title to a posting that is succinct enough. I would like to think that I have succeeded in that area, but surely there must be a better way, such as th e option to use some sort of Boolean perimeters?

---

### Post by steve.horsley on 2006-06-21
Urgh! 

You are right to not try a reinstallation. The best approach is to get the data off without touching the original disk at all.

First, I suggest using a live CD to copy the data from your hard disk to a USB stick. You could do this with a Ubuntu live CD. I don't remember if the Ubuntu live CD puts an icon on the desktop for every partition. If it doesn't, for a beginner, it might be easier to use a knoppix live CD which I know does do this. Knoppix normally opens existing drives read-only, but right-clicking the icon allows you to set read-write, so you could start copying files to other drives if you wanted. Both Ubuntu and Knoppix should spot when you insert a USB stick. You may have to tinker with your disk master/slave jumpers to get the old partition visible again (hoping it's not been overwritten). 

I assume you know where your pictures are, so could copy those off without problems. Thunderbird files are kept in a hidden folder in your home directory, called **.mozilla-thunderbird** I think. In Ubuntu, you can get to see hidden files/folders by typing Ctrl-H into nautilus (the file manager). In konqueror (knoppix file manager) it's in the configuration menus somewhere. If you copy the whole .mozilla-thunderbird directory, you will be able to copy it back after recovering a working Linux system and all your mails/preferences will be there. 

As for recovering a working O/S, this could take rather longer than just installing Kubuntu over the top. It's kind of difficult to know what's gone wrong with the existing install.

You can download live CD iso images here:
[http://www.knoppix.net/get.php](http://www.knoppix.net/get.php)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

As you reinstall, can I suggest that you use a separate partition for /home? This allows reinstallation of the OS without trashing your home folder and all its contents.

---

### Post by Michael Pollock on 2006-06-25
Thanks for the feedback and recommendations. I am following through, but until I moved to a different computer, couldn't log in to download either Ubuntu or Knoppit.

As a result, I am beginning to think that the problem may be, if not totally, then at least in part, because the hard drive is beginning to fail, and that the failure may even have something to do with the mother board--i.e., the board may have been "damaged" as a result of my initially installing an OS (Win98) it would not fully support, then trying to configure it with hardware it also would not fully support. As my burner has also apparently failed (did I unintentionally damage it moving it from the machine in which it was installed to another as networking the machines was not possible under these circumstances?), I have ordered the Live CD from ShipIt in the event that I am unsuccessful using a burner in another machine to which I have access in a local, private, library (it will be closed for a good part of July for custodial maintenance and upgrades, so if I fail there, I might well have the CD from ShipIt before I would have a second chance to burn one for myself).

I cannot be certain that the drive is failing--because the drive was formatted for Linux without a FAT32 partition, none of my Windows machines will allow me to access the drive in the way I would need to do in order to make that determination, in large part because with no more then I want to recover on the drive in terms of total number of bytes, (well?) under 100M, I loathe the idea of having to buy another drive that is 100G or more without being more confident than I am that I would not damage the "new" drive in process, but I have been unable to find any drives, new or used, any smaller than that.

Your thoughts on either whether the drive is failing and whether any of the prior advice you gave for resolving the problems may need to be "twiqued" as a result would be appreciated.

---


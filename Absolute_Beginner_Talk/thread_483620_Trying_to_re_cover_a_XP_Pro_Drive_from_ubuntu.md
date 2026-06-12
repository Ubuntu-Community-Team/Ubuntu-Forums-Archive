---
title: "Trying to re cover a XP Pro Drive from ubuntu"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by red777 on 2007-06-24
I have my wifes hard drive in my PC as a slave drive.She has done something to it & removed all access.I have several recovery tools available on CD/DVD etc but all are written in Windows & when I try to use them I get this message.Can any one advise B4 she gets too angry.
Thanks

The filename "pci_filerecovery.exe" indicates that this file is of type "executable". The contents of the file indicate that the file is of type "DOS/Windows executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "DOS/Windows executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

It's the bit about renaming I don't understand or if there's a program that will do this automatically,I really hate having to use windows,I can never get it to work:(:(

---

### Post by cogadh on 2007-06-24
Have you tried using Recovery Console on your original XP install CD to correct the problem? If it won't boot, sometimes just running "fixmbr" from the Recovery Console can correct it. Don't run it in your Linux PC, it will wipe out your GRUB install.

---

### Post by red777 on 2007-06-24
Yep I tried that, but I can't get her cd player to read any discs, so I'm doing the best I can without taking the whole thing to a pro shop.I have heaps of recovery tools but I can't get Ubuntu to run them as per above so any more ideas please.

---

### Post by moffa on 2007-06-24
You could try running Windows apps using wine.  Not sure how well it would work.  I would recommend installing  Wine and NTFS Configuration Tool.  Maybe you can read the files that way.

---

### Post by cogadh on 2007-06-24
You sound like you know what you are doing, so please don't be offended if I ask some stupid questions to clarify some things. 

You said her PC won't read CDs, is her BIOS configured to boot from the CD? You won't be able to get into Recovery Console if it isn't. Also, is her hard drive even detected by the BIOS correctly? If not, the hard drive or IDE controller may be bad.

I don't mean to keep pushing the XP Recovery Console option, but AFAIK, there aren't any ways to recover a corrupted Windows install using Linux.

---

### Post by totheresq001 on 2007-06-24
You can use knoppix to recover data off the drive-then wipe and reload it checl out this link
[http://www.extremetech.com/article2/0,1697,1918391,00.asp](http://www.extremetech.com/article2/0,1697,1918391,00.asp)

---

### Post by red777 on 2007-06-24
Hey  I don't mind any suggestions,it's been so long since I built her system I can't remember what I set up,apparently she has inserted the XPPro disc & may have re formatted the drive then at some point she's stopped the process or not set up a USER. I have the tools to rebuild all the programmes but I don't have a spare safe PC to do it on,so I'm attempting this on my PC to see if it will work.I have WINE etc on this PC but haven't used it so maybe I've asked this question the wrong way.How do I enable the DOS/WINDOWS Exe files to run.

---

### Post by cogadh on 2007-06-25
The only way to run a Windows executable in Linux is through Wine. If you already have Wine installed and configured, then all you have to do is enter this in a terminal:
```
wine /path/to/windows/executable.exe
```
Obviously, change the path to match what you are trying to run. There is no guarantee that this will work, Wine is still beta software and not everything that runs on Windows will run in Wine.

If the executable you are trying to run is DOS executable, then you should try installing and using DOSBox instead of Wine.

---

### Post by Neobuntu on 2007-06-25
You should not recover an XP drive that may have mal-ware.

Back up the data that you can't live without. You can do that from Ubuntu; after access to the drive is turned on.

Consider moving (her) to Ubuntu or Kubuntu with a clean install. 

If you want a dual boot, clean install XP first. The problem is, legally you'd need (save time) to BUY an expensive copy of Windows, paying more for "pro" version and more to include a newer version (to save update time). There are many roadblocks and technical work-a-rounds to build up Windows from an old copy.

Even if you do all this (takes lots of time but a clean install is faster than a "clean up"), Windows security is still questionable compared to (K)Ubuntu. 

PLEASE do not feed the Microsoft.

This may not be what you want to hear, and you may not have been clear about what you want but you should know that Windows can not be "cleaned".

Obviously, if you hear the advise I'm giving, the deck is stacked, to drive you toward a new system and where Microsoft gets their "tax" for pre-installing. Yet the truth is, that a Windows system is just the beginning of customization. Where the open systems takes far less time to install AND hits the ground running. Just make sure your system does not have cheap hardware devices that only work with Windows.

---


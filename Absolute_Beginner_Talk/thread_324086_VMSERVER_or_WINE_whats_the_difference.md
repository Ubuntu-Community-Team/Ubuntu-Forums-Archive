---
title: "VMSERVER or WINE whats the difference?"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by andytof47 on 2006-12-23
Hi I want to know if I should be using VMserver or WINE?

basically I want to use the windows 98 environment for some old kids games that just don't run under XP - can i install extra programs such as the said old game into WINE?

and secondly I want to access my Outlook that is already installed on XP(Dual Boot) but I don't understand wether or not I can access it via VMserver? Do i have create a fresh WEXP or can i point it to my existing one?

Cheers

---

### Post by OffHand on 2006-12-23
> **andytof47 said:**
> Hi I want to know if I should be using VMserver or WINE?

basically I want to use the windows 98 environment for some old kids games that just don't run under XP - can i install extra programs such as the said old game into WINE?

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Not every application will run with WINE. Check the app database in the link I posted.

---

### Post by andytof47 on 2006-12-23
cheers off hand

Just wondering now how can I install this application to see if it works?

thanks again:D

---

### Post by stanjam on 2006-12-23
Wine and VMSErver are both emulators of a sort but there are big differences.  Wine emulates certain Windows functions so that you can run Windows programs.  VMWare allows you to actually run Windows on top of Ubuntu.  

So the odds of a program running under VMServer are much greater because you are actually RUNNING windows.  However programs will most likely run facster under Wine since wiuth VMware products you are devoting resources to run bot Operating systems!

Hope that clears it up some.

---

### Post by maddog39 on 2006-12-23
> **stanjam said:**
> Wine and VMSErver are both emulators of a sort but there are big differences.  Wine emulates certain Windows functions so that you can run Windows programs.  VMWare allows you to actually run Windows on top of Ubuntu.  
Wine isn't an emulator, its an implementation of the windows API on top of the X window system. So techinically its running those apps native.

---

### Post by RudolfMDLT on 2006-12-23
Install a brand new XP in VMware, export your mail from the original XP and Import into the new Virtual XP. Same goes for user profiles, my documents - Windows actually has a tool for this, I think it&#347; called migration Wizzard to help you make you New XP box look  like the old one with all your favorites and documents. It´s under accessories I think.

---

### Post by gn2 on 2006-12-23
> **RudolfMDLT said:**
> Install a brand new XP in VMware, export your mail from the original XP and Import into the new Virtual XP. Same goes for user profiles, my documents - Windows actually has a tool for this, I think it&#347; called migration Wizzard to help you make you New XP box look  like the old one with all your favorites and documents. It´s under accessories I think.

Files and Settings transfer Wizard.

Here is the info you need: [http://www.microsoft.com/technet/prodtechnol/winxppro/deploy/mgrtfset.mspx](http://www.microsoft.com/technet/prodtechnol/winxppro/deploy/mgrtfset.mspx)

---

### Post by Patrick-Ruff on 2006-12-23
I read that wine was an "emulation layer" program, I see emulation!  regardless, VMWARE = running another OS in a window (or fullscreen if you want) while already running another OS.  

it'd be like basically running windows and having Linux being ran in a window :P.

---

### Post by andytof47 on 2006-12-23
All is crystal clear now!!!!

I will ponder what to do now!!!!!!1


Merry Christmas all

---

### Post by macogw on 2006-12-23
> **Patrick-Ruff said:**
> I read that wine was an "emulation layer" program, I see emulation!  regardless, VMWARE = running another OS in a window (or fullscreen if you want) while already running another OS.  

it'd be like basically running windows and having Linux being ran in a window :P.

**W**ine **i**s **N**ot an **E**mulator

---

### Post by xabbott on 2006-12-23
> **Patrick-Ruff said:**
> I read that wine was an "emulation layer" program, I see emulation!  regardless, VMWARE = running another OS in a window (or fullscreen if you want) while already running another OS.  

it'd be like basically running windows and having Linux being ran in a window :P.

It's not an emulator at all. You do not take a performance hit running a Windows application under Wine like you would an emulator. In any case, if possible always try wine first. If you can't get it to run with Wine then yea, use VM.

---


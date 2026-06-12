---
title: "MS Programs with Wine"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by H3lix on 2007-08-10
Hi guys. I've been trying to get Wine to run some programs and have failed miserably at the following:

MSN Messenger Live
MSN Messenger 6 - was close got the icon to load on the tray for 1 second
Microsoft Office 2007

My question is should they be able to run and if so how?  I've tried downloading some DLL's but they're still not working. Further more though I need MSN for my contacts, are there any alternatives to MS Word 2007, I like it due to the equation tool which allows me to present my equations quickly and easily, when I last checked alternatives like Open Office doesn't have these.  Also to save time, do the following programs work with Wine:

Matlab 
SolidWorks
Photoshop CS3

I hope these do work otherwise my record of being Windows free will be about 1 day :( , unless there are viable alternatives...

Thanks

---

### Post by splintercellguy on 2007-08-10
There's always dual-booting, have you peeked at Wine AppDb at all [http://appdb.winehq.org/?](http://appdb.winehq.org/?) Instead of using MSN Messenger (which doesn't work all that well under Wine), why not Pidgin, aMSN, or other alternative clients? Microsoft Office might work but have you looked at OpenOffice.org? Matlab seems to work well, SolidWorks what edition? [http://appdb.winehq.org/appview.php?iAppId=318](http://appdb.winehq.org/appview.php?iAppId=318) Photoshop CS3 not so much, GIMP might be a replacement or you could dual-boot.

---

### Post by Steveway on 2007-08-10
Well, for 1 & 2:
Pidgin or Amsn, pick your choice.
For 3:
Open Office, (Though I only use Abiword)
4: Afaik there is a Matlab version for Linux
5: Never heard of it.
6: The Gimp

EDIT: Curse you Splintercellguy. :)

---

### Post by H3lix on 2007-08-10
Solidworks 2003 - you could say I've had some kind of success with the MS Office 2007 install in that I get a microsecond flash of the installer but then it crashes with a Windows error and an option to send it to Microsoft :D, I don't know it=f this helps but here are the last few lines on my terminal after downloading gdiplus.dll and copying it to system32 and running setup:

err:eventlog:ReportEventW L"rosebud.en-us_setup.xml"
err:eventlog:ReportEventW L"x"
err:eventlog:ReportEventW L"x"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:actctx:QueryActCtxW 80000010 0x3008bb0c (nil) 1 0x7d2f56b8 8 (nil)
fixme:reg:GetNativeSystemInfo (0x34fc5c) using GetSystemInfo()
fixme:powrprof:DllMain (0x7d1e0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d1e0000, 0, (nil)) not fully implemented
fixme:netapi32:NetGetJoinInformation Stub (null) 0x34fc84 0x34fc78
fixme:advapi:CheckTokenMembership ((nil) 0x180018 0x34fc60) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x180018 0x34fc60) stub!
fixme:nls:GetUserGeoID 16

Thanks again

---

### Post by splintercellguy on 2007-08-10
No luck for Office '07, I don't see any AppDb entries for SolidWorks '03, maybe you could be the first to file an entry? :)

---

### Post by poisonkiller on 2007-08-10
I decided not to make a new thread for my problem with Wine. Ubuntu has been installed on my computer for 12 hours, so i'm a total newbie. I have installed Wine, but after installing a  lot more stuff all Wine icons are gone from Applications->Accessories and System->Preferences, so I can't modify Wine. I can run Windows applications, but I want to configure Wine. Thanks for help!

---

### Post by WebSiteGuru on 2007-08-10
Piggy back on what splintercellguy said about Photoshop CS3. All  CS3 apps required WinXP SP2 for them to work, Not unless the latest wine will be compatible to WinXP SP2. You will have to dual boot it.

I, myself, got used to Photoshop. So, I know how you feel.

---

### Post by rye_ on 2007-08-10
hi,

a linux form of matlab exits, also comes bundled with student version.
however, octave and scilab are both excellent alternatives, I prefer octave.

to my knowledge wine won't help with matlab.

ryan

---

### Post by H3lix on 2007-08-10
Hey hey I've had it for bout that type winecfg in your terminal (app>Accessories>terminal)

Edit:  Thinking bout it my programming professor is a Linus user and he taught all his classes of Matlab on Madriva Linus so I should be OK i think.  If I can get SolidWorks to work (bout to try) and someone can suggest a word processor with easy equation symbol entry I'll be happy - nice to know other people are in the same boat - no doubt Linux will be eventually be able to run these programs (hopes)

---

### Post by splintercellguy on 2007-08-10
> **poisonkiller said:**
> I decided not to make a new thread for my problem with Wine. Ubuntu has been installed on my computer for 12 hours, so i'm a total newbie. I have installed Wine, but after installing a  lot more stuff all Wine icons are gone from Applications->Accessories and System->Preferences, so I can't modify Wine. I can run Windows applications, but I want to configure Wine. Thanks for help!

To launch Wine Configuration, Alt-F2 and type winecfg. You can edit the Main Menu manually and add the icons as desired.

---


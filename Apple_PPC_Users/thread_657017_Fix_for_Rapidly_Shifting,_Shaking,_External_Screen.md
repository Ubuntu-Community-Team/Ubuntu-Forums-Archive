---
title: "Fix for Rapidly Shifting, Shaking, External Screen Problem?"
date: 2008-01-03
forum: Apple PPC Users
---

### Post by zeeb on 2008-01-03
Hi All ---

wow.  Just found this site --- what a cool place.    

I'm hoping someone here may have some info regarding an external screen problem I'm having when connected to my P.Book 1.25ghz.    After a second logicboard replacement, my external screen moves rapidly from side to side after about 20 mins of usage.  It seems to start happening when shifting any open window or application and then continues to do so by itself.  After awhile, re-booting is the only option - v. boring.    The external screen is a Samsung, eight months old and has been fine when used w/ both previous logicboards.

The Apple Extended Hardware Test says the logicboard - and I 'assume' also the ATI Radeon 9600 vidcard - is A-OK.  I'm curious if there's a specific vid-card diagnostic test I can run - I've installed chud and developer tools, I just dont know where to begin with them...

This happens on the P.Book internal drive w/ Tiger 10.4.10 or when booted from two different ext. HDDs - one with 10.3.9, another w/ 10.4.10.    I have tried dumping lots of plists and also created a new user account - the shakes continue.   I really hope its a conflict or something other than another logicboard replacement.      boo.

Is it possible the installed 10.4.10 OS is causing this across all system boots?

Unfortunately, I'm not v. familiar how the .plists .kexts or bundles (?) work in relation to the external screen - I'd be most grateful if someone could lend me a hand with some file info.  I have listed the tests and utilities I've tried below - the Graphic card spec is below that.

Due to the logicboard repairs and endless troubleshooting, I have re-authorised my computer maybe four times now with itunes, so I'm almost out of range for music usage if I re-install the OS again.   If there is a way to fix or re-set the card without having to re-install again, please let me know!

Many thnx in Adv -- Happy New Year to all 

Cheers,

John.


The Utilities and options I have tried are;?
- Disk Utility / Repaired permissions
- Apple Hardware Test
- PMU Reset
- PRAM Reset
- NVRAM Reset via open firmware
- booting from external Drives with OSX 10.3.9 and alternate 10.4.10
- DiskWarrior - repaired permmissions / rebuilt directory
- tried updates from AMD site for ATI 9600 videocard
- tried alternate arrangments of the screen in system prefs. > displays > arrangement
- created new user account
?** I am narrowing it down to poss. one of these files or locations---? **??Library > Prefs??com.apple.windowserver.plist?com.apple.loginwindow.plist?com.apple.HIToolbox.plist?com.apple.BezelServices.plist?com.apple.dockfixup.plist??Library > Prefs > System configuration ??com.apple.airport.preferences.plist?com.apple.nat.plist?com.apple.PowerManagement.plist?NetworkInterfaces.plist?preferences.plist??there are numerous places with 'things i could dump' (!!) in the 'X' System folder too - i.e.; ??Displays ?Extensions ?Frameworks ?Monitor Panels ?Preference Panes ?Start-up Items?System Configuration etc....

The graphic/video specs are;

ATI Mobility Radeon 9600:

Chipset Model: ATY,RV350M10
Type: Display
Bus: AGP
VRAM (Total): 64 MB
Vendor: ATI (0x1002)
Device ID: 0x4e50
Revision ID: 0x0000
ROM Revision: 113-xxxxx-117
Displays:
Color LCD:
Display Type: LCD
Resolution: 1280 x 854
Depth: 32-bit Color
Built-In: Yes
Core Image: Supported
Mirror: Off
Online: Yes
Quartz Extreme: Supported

SyncMaster:
Resolution: 1440 x 900 @ 60 Hz
Depth: 32-bit Color
Core Image: Supported
Main Display: Yes
Mirror: Off
Online: Yes
Quartz Extreme: Supported
Rotation: Supported

---


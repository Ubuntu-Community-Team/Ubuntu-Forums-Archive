---
title: "Linux Pwned My Computer"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by IkickPigeons on 2007-03-13
I really wanted to like Linux. I really did. I tried so hard to like it. But now I hate it. I didn't even get it installed on my system and I couldn't even load it on my system through the Live CD. I knew that it would take some time in order to get it to work, but I didn't expect it to render my computer (xp pro) useless.

The problem I had with Linux has now miraculously transfered to my xp, without ever being installed!!!

Before, i couldn't load the Live CD because I have an ATI card. When it did finish loading, I would only see a black screen. Well boys and girls, now when I load my xp I get the same exact thing!!! 

WTF

This is how it may have happened.

In my desperation to try to get the Live CD to alteast boot, I tried to disable my ATI X1900xtx GPU and run on the integrated graphics controller. Man was that a mistake. Now I went into BIOS and changed what I believe to the setting to switch from Integrated to peripheral. I switch from PCI to "PEB". Tried to boot up linux. No go. Then went back to BIOS and switched it back to PCI from "PEB". And now this problem happens. I even hear the normal sounds when loading into xp. I just cant see a damn thing.

PLEASE.................

 How do I get my xp OS back and never have to deal with this none sense ever again? 

A better yet, if you can solve my original problem with linux then you get enough cookies for three lifetimes.

Then, maybe, maybe, I will forgive linux and make the switch.

---

### Post by nalmeth on 2007-03-13
If you are sure the LiveCD is not corrupt, start it with SAFE-GRAPHICS mode rather than the regular Start/Install Ubuntu.

I don't know what to do about your Windows, I know little-nothing about the system.

Do tell if this works or not.

---

### Post by esaym on 2007-03-13
> **IkickPigeons said:**
> I really wanted to like Linux. I really did. I tried so hard to like it. But now I hate it. I didn't even get it installed on my system and I couldn't even load it on my system through the Live CD. I knew that it would take some time in order to get it to work, but I didn't expect it to render my computer (xp pro) useless.

The problem I had with Linux has now miraculously transfered to my xp, without ever being installed!!!

Before, i couldn't load the Live CD because I have an ATI card. When it did finish loading, I would only see a black screen. Well boys and girls, now when I load my xp I get the same exact thing!!! 

WTF

This is how it may have happened.

In my desperation to try to get the Live CD to alteast boot, I tried to disable my ATI X1900xtx GPU and run on the integrated graphics controller. Man was that a mistake. Now I went into BIOS and changed what I believe to the setting to switch from Integrated to peripheral. I switch from PCI to "PEB". Tried to boot up linux. No go. Then went back to BIOS and switched it back to PCI from "PEB". And now this problem happens. I even hear the normal sounds when loading into xp. I just cant see a damn thing.

PLEASE.................

 How do I get my xp OS back and never have to deal with this none sense ever again? 

A better yet, if you can solve my original problem with linux then you get enough cookies for three lifetimes.

Then, maybe, maybe, I will forgive linux and make the switch.

Have you tried clearing the bios using a jumper on the motherboard?  Also buy nvidia.  I only support manufactures that support linux :p  I just picked up a 6800 for $50 the other day :)

---

### Post by IkickPigeons on 2007-03-13
I already tried before and after the incident

I dont care about getting Ubuntu to work anymore. I just want to get my computer back. I need it really soon because of school work. My thesis is on there and well... I like my thesis. And I dont want to type a 20 page paper all over again. 

Am I asking too much?

---

### Post by Songwind on 2007-03-13
> **IkickPigeons said:**
> 
In my desperation to try to get the Live CD to alteast boot, I tried to disable my ATI X1900xtx GPU and run on the integrated graphics controller. Man was that a mistake. Now I went into BIOS and changed what I believe to the setting to switch from Integrated to peripheral. I switch from PCI to "PEB". Tried to boot up linux. No go. Then went back to BIOS and switched it back to PCI from "PEB". And now this problem happens. I even hear the normal sounds when loading into xp. I just cant see a damn thing.


Do you have two different VGA or DVI ports on your system?  Did you switch to the other one during any of your tests?

This sounds like something that happened (all under windows) to my gf's computer.  It started using the onboard video instead of the PCI card video and we were all wigged out for a bit until we remembered to switch back to the other VGA plug, and there was Windows like normal.  we changed the settings so that Windows chose the other card, rebooted, and everything was fine.

---

### Post by IkickPigeons on 2007-03-14
I made sure to plug my DVI correctly in the back of my card.

I bought an ATI card because at the time it was the fastest and I get a super good deal on it. And if i have experienced this many problems without linux actually installed... I cannot begin to think of the problems if and ever i decide to instal it. 

I redid everything i changed.

I just have a feeling that the seeting I changed in my BIOS was someting completly different than what i thought it was.

---

### Post by IkickPigeons on 2007-03-14
im about ready to kill someone....

I know its in the right DVI plug becasue i see the POST screen and the windows boot up image. Its just that right when the system switches to windows, when you hear the little tune, i get a balck screen and nothing. WTF!!!111

---

### Post by nalmeth on 2007-03-14
Did you change the Video RAM settings?

There should be a setting in your BIOS that will change how much onboard RAM is allocated to your video card. Perhaps when you switched to the onboard, that setting was reset, and when you changed it back, there wasn't enough for the ATI card.

It's an idea :(

EDIT:
> And if i have experienced this many problems without linux actually installed... I cannot begin to think of the problems if and ever i decide to instal it.
If you didn't install Ubuntu, it couldn't have done anything to your Windows install. Something else is the cause. Don't jump to conclusions.

---

### Post by IkickPigeons on 2007-03-14
alright maybe im blaming Ubuntu for something that i did. But hell. Ive tried installing it for over a week now...

---

### Post by silhouette on 2007-03-14
Isn't there a way to reset BIOS settings? Like powering off the computer, taking out the battery in the mobo for a couple of hours, then putting it back in and re-powering on the computer?

---

### Post by maniacmusician on 2007-03-14
> **IkickPigeons said:**
> alright maybe im blaming Ubuntu for something that i did. But hell. Ive tried installing it for over a week now...
right; but it certainly isn't Ubuntu's fault that you screwed up.

Does your BIOS have a return to defaults option somewhere? Most do. If you're not sure or can't find it, try google for your motherboard and BIOS version and see what you get.

---

### Post by nalmeth on 2007-03-14
> Isn't there a way to reset BIOS settings? Like powering off the computer, taking out the battery in the mobo for a couple of hours, then putting it back in and re-powering on the computer?
This is a way to reset the BIOS if you set a BIOS password and forgot it. As manicmusician said there should be a way to do it in less drastic fashion.

Random note: don't set a BIOS password :) I know all to well it's not worth it.

---

### Post by Prof.Arronax on 2007-03-14
> **silhouette said:**
> Isn't there a way to reset BIOS settings? Like powering off the computer, taking out the battery in the mobo for a couple of hours, then putting it back in and re-powering on the computer?

Almost every computer has a jumper (usually one with 3 pins with a jump plug covering 2 of them) that will clear the BIOS and restore it to the chip's default.  It should only take a few seconds of the jumper in the "clear" position to get back to factory default.  If you don't have the motherboard manual, many boards have (albeit small) print showing the "normal" and "clear" positions on that jumper.

---

### Post by gldvxx on 2007-03-14
try starting xp in safe mode  and reinstalling the ati drivers.  to boot windows in safe mode, either hold down both shift keys or keep tappin F8, you could google it i guess haha i don't really remember the exact keys or when you push them.  you should get a safe mode menu, there should be an option to boot into safe mode with network.  choose that option so that you can connect to the network and download a new driver.  it's possible your driver has gotten corrupted - windows is verrrrry finicky, anything can set off anything.. it could be that your graphics card is bad, maybe you spilled something on your motherboard?   maybe before this happened it wasn't shut down properly?  in any case, you should be familiar with your device manager and managing drivers through that before you attempt to install ATI drivers.  if you are not, then i don't think this forum can help you unless you install ubuntu ;D

when you booted the system using the onboard card, did you switch your dvi port to use the onboard dvi port, or were you still trying to use the ati card's dvi port?

another question, i didn't understand your original post - you said you "loaded" the cd, did you run the install or just try to boot from it?

---

### Post by IkickPigeons on 2007-03-14
> **gldvxx said:**
> try starting xp in safe mode  and reinstalling the ati drivers.  to boot windows in safe mode, either hold down both shift keys or keep tappin F8, you could google it i guess haha i don't really remember the exact keys or when you push them.  you should get a safe mode menu, there should be an option to boot into safe mode with network.  choose that option so that you can connect to the network and download a new driver.  it's possible your driver has gotten corrupted - windows is verrrrry finicky, anything can set off anything.. it could be that your graphics card is bad, maybe you spilled something on your motherboard?   maybe before this happened it wasn't shut down properly?  in any case, you should be familiar with your device manager and managing drivers through that before you attempt to install ATI drivers.  if you are not, then i don't think this forum can help you unless you install ubuntu ;D

when you booted the system using the onboard card, did you switch your dvi port to use the onboard dvi port, or were you still trying to use the ati card's dvi port?

another question, i didn't understand your original post - you said you "loaded" the cd, did you run the install or just try to boot from it?


I got the system to boot in safe mod. Does this mean my card isnt dead? This would be bad news because the card is relatively new and expensive. 

Ill try to dl the ati drivers.

To answer your question:

No i didnt spill anything on my mobo

No i do not shutdown my computer by unplugging it

No I only tried to run on integrated for ubuntu

Yes i tried to boot from the CD not install

What is a definative test that i can run to see if my card is in fact dead?

---

### Post by comwiz7 on 2007-03-14
1. What I would do is take out the hard drive and put it in another Windows Computer (not hard to find)

2. Copy your important files off of it. When your sure you have everything, format the hard drive. 

3. Verify your computer BIOS settings are correct, same for the motherboard jumpers, and then reINSTALL the OS of your choice. As for your linux issue, I'm not sure.

---

### Post by v8YKxgHe on 2007-03-14
> **IkickPigeons said:**
> im about ready to kill someone....

I know its in the right DVI plug becasue i see the POST screen and the windows boot up image. Its just that right when the system switches to windows, when you hear the little tune, i get a balck screen and nothing. WTF!!!111

I have had this trouble many many times with Windows and I can tell you now it has nothing to do with Ubuntu. How do I know? Because my Windows install is on a separate hard drive that is _always_ disconnected when I use Ubuntu, and Ubuntu is disconnected when I use Windows. 

I to have an ATI card and believe it is something to do with the drivers. I got so annoyed at it somedays, it took like 7 reboots of Windows for it to finally load the GUI. I did find a quick 'fix' though, when I wanted to boot into Windows I would go into the BIOS and just hit F10 to save the BIOS again, it then worked.... most of the time. 

I've recently just done a fresh install of Windows (XP decided to remove licensing of every program I own .... nice) and with the latest ATI drivers this works fine. I suggest you boot into safe mode for Windows and download and install the latest ATI Drivers, this should fix it. 

I guess Windows just isn't ready for the desktop, I mean how are people suppose to know what to do with no GUI, doesn't even kick you out to CLI! I guess the Windows year will never come. :)

---

### Post by igknighted on 2007-03-14
> **IkickPigeons said:**
> I really wanted to like Linux. I really did. I tried so hard to like it. But now I hate it. I didn't even get it installed on my system and I couldn't even load it on my system through the Live CD. I knew that it would take some time in order to get it to work, but I didn't expect it to render my computer (xp pro) useless.

The problem I had with Linux has now miraculously transfered to my xp, without ever being installed!!!

Before, i couldn't load the Live CD because I have an ATI card. When it did finish loading, I would only see a black screen. Well boys and girls, now when I load my xp I get the same exact thing!!! 

WTF

This is how it may have happened.

In my desperation to try to get the Live CD to alteast boot, I tried to disable my ATI X1900xtx GPU and run on the integrated graphics controller. Man was that a mistake. Now I went into BIOS and changed what I believe to the setting to switch from Integrated to peripheral. I switch from PCI to "PEB". Tried to boot up linux. No go. Then went back to BIOS and switched it back to PCI from "PEB". And now this problem happens. I even hear the normal sounds when loading into xp. I just cant see a damn thing.

PLEASE.................

 How do I get my xp OS back and never have to deal with this none sense ever again? 

A better yet, if you can solve my original problem with linux then you get enough cookies for three lifetimes.

Then, maybe, maybe, I will forgive linux and make the switch.

No offense intended here, but WTF are you doing changing BIOS settings that you don't know what do?  If you don't want to use your gfx card, just pull it out.  Easy as pie.  To mess around on a computer with stuff like your 20pg thesis on it is rather foolish.  I hardly think you can fault linux here however.  You went into your BIOS and messed around and caused issues, how was linux at fault?  Because your ATI card didn't work?  There are much much easier fixes for that if you had looked around.  All this said, I will try to help:

Where are you pluging your monitor in?  If it is blank on the card, did you try the Mobo?  Vice versa?  Try pulling your card out all the way.  The booting with the integrated video.  If this works, then you at least have a system to start with.

---

### Post by lahook on 2007-03-14
when you boot in safe mode does everything seem to be there? just ugly
check your video card  in device manager and try to update driver. (see if it says you're using the best one)
then try to boot in normal mode
if it works you're good to go 
if not you might try booting your xp cd and select repair

as far as linux live cd's i try several different ones if it don't boot up i move on.
my home computer which is running unbuntu feisty has a problem with a lot of live cds. ie mandriva, gentoo, mepis, sidux, and katonix.
my laptop at work likes all live linux cd's i've tried

don't give up on linux yet

hope this helps

---

### Post by IkickPigeons on 2007-03-14
Just to let your guys know. I'm not an idiot when it comes to hardware, just programing and OS's. I know which DVI plug to plug into and I know my way around a BIOS. I did infact build five computers before. I'm just really damn paranoid that my video card just died. 

Hopefully when I do a fresh install of the ATI drivers I can get it to work. Hopefully. If this doesnt work, Im gonna reset my BIOS and lose my OC. If that doesnt work. Swap out the hardrive.

The system did manage to boot in safe mood. The resolution was at the lowest and the gui was that of windows 98.

---

### Post by robholt on 2007-03-14
IkickPigeons-

I'm going to come to your defense here on a number of points:

1. Ati is a damn good graphics card for a *Windows* machine - you weren't buying hardware strictly for Linux when you put your system together. I'm sorry Ati hasn't done a good job of producing drivers for Linux, but we all know what fuels that market and gaming is not a Linux forte. You bought your x1900xtx because it is a very good gaming card, like I bought my x1900xt for the same reason - you weren't thinking about Linux for that.

2. I mess around in my bios all the time and if you just switched from onboard intergrated graphics to a add-in card, I don't think it was anything you did in the bios, so I don't know why you would reset the bios. You should only have the option of disabling the onboard graphics (just like you would if you had onboard sound and wanted to use a sound card of your choice instead) and you should have the option of first display being either pci or peg, neither of those settings are going to screw you up. Don't worry about the memory allocation thing, if you have the option of settnig it, make sure its at 128.

If your getting to the Windows welcome screen, and then it goes black, it is a problem inside the OS loading the video drivers, not the bios messing you up! It's quite possibe the drivers got corrupted in your changing from onboard graphics to the x1900xtx. I would try booting into safe mode, unistall everything for ati in add/remove programs, go back into your bios and make sure that the onboard graphics are disabled, reboot and reload your drivers. 

Your facing the same decision I am now, because your finding out that hardware that worked fine in XP are going to be more difficult to deal with in Linux. Yeah, you could go out and get a cheap Nvidia card, but you have a perfectly good one now.

To me, it all boils down to how bad I want to get out from under Microsoft.

---

### Post by IkickPigeons on 2007-03-14
> **robholt said:**
> IkickPigeons-

I'm going to come to your defense here on a number of points:

1. Ati is a damn good graphics card for a *Windows* machine - you weren't buying hardware strictly for Linux when you put your system together. I'm sorry Ati hasn't done a good job of producing drivers for Linux, but we all know what fuels that market and gaming is not a Linux forte. You bought your x1900xtx because it is a very good gaming card, like I bought my x1900xt for the same reason - you weren't thinking about Linux for that.

2. I mess around in my bios all the time and if you just switched from onboard intergrated graphics to a add-in card, I don't think it was anything you did in the bios, so I don't know why you would reset the bios. You should only have the option of disabling the onboard graphics (just like you would if you had onboard sound and wanted to use a sound card of your choice instead) and you should have the option of first display being either pci or peg, neither of those settings are going to screw you up. Don't worry about the memory allocation thing, if you have the option of settnig it, make sure its at 128.

If your getting to the Windows welcome screen, and then it goes black, it is a problem inside the OS loading the video drivers, not the bios messing you up! It's quite possibe the drivers got corrupted in your changing from onboard graphics to the x1900xtx. I would try booting into safe mode, unistall everything for ati in add/remove programs, go back into your bios and make sure that the onboard graphics are disabled, reboot and reload your drivers. 

Your facing the same decision I am now, because your finding out that hardware that worked fine in XP are going to be more difficult to deal with in Linux. Yeah, you could go out and get a cheap Nvidia card, but you have a perfectly good one now.

To me, it all boils down to how bad I want to get out from under Microsoft.


Robholt thank you for the support.

Ill try re-installing my drivers when i get the chance. Still busy with my damn schoolwork...

Well at least i know that if i do want to run Linux i better get an Nvidia card. Maybe I'll upgrade when Crysis comes out.

---

### Post by IkickPigeons on 2007-03-14
*UPDATE*

I got my computer un-pwned half way. Currently getting the drivers installed. But now it boots fine in normal non-safe mod. 

Thanks to all who suggested to re-install the driver. I guess they got corrupted somehow. :confused: 

Anyways. I'm back Microsoft.

---

### Post by esaym on 2007-03-15
How did you try to install ubuntu?  Did you use 2 different hard drives?  Or did you only use one hard drive?  It sounds like you only used one hard drive.  So you tried to load the live cd and it wouldn't work?  So then you changed some video settings in the bios and then you tried again?  After that not working you tried to boot into windows?

Only thing I think that happened would be that windows tried to load using your onboard video and that caused some kind of driver glitch.  Other then that your hard drive might be going dead.  You might want to install hdtune: [http://www.hdtune.com/](http://www.hdtune.com/) and check out the info under the health tab.  Post us a picture if you need anyhelp:)

---

### Post by gldvxx on 2007-03-19
> **IkickPigeons said:**
> *UPDATE*

I got my computer un-pwned half way. Currently getting the drivers installed. But now it boots fine in normal non-safe mod. 

Thanks to all who suggested to re-install the driver. I guess they got corrupted somehow. :confused: 

Anyways. I'm back Microsoft.

i'm glad you got your computer working again!  listen, nobody here thinks you are in anyway stupid or incompetent with computers!!  :D  i may have asked "stupid" questions because i'm just trying to cover all the bases.  i'm a pretty advanced computer user and even i do stupid things (you don't know how many times "is it plugged in" has applied to ME).  

a word of advice - back up your thesis!!!!!!!!!!  save it to a disk, 2 disks, 3 disks, if you have a web based email or some kind of IMAP repository, email it to yourself after each time you work on it.

don't give up on ubuntu!  sounds like the problem you had was getting windows and ubuntu to play nicely together, and maybe doing this install in the middle of a busy quarter/semester was not the best idea.  try playing with it when you have some downtime.  good luck!

---


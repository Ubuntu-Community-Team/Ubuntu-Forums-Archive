---
title: "Problems with the KDE installation and my laptop, can anyone help?"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Jay Jay on 2006-04-15
Hi, I'm a total novice to the Linux world. Up untill now my main experience has been with Windows and I'm trying to adjust to doing things differently now. :)  The other day I installed KDE 5.10 on my HP Omnibook 6000 laptop and so far I'm glad I made the switch, however there are few niggling issues that due to my lack of knowledge I am unable to resolve...

When I insert my Netgear WG511 v2 card, It's totally dead - KDE doesn't acknowledge It's presence, there are no lights on the card (I know that it works because I use it all the time with my Sony Vaio). My ethernet port is listed as "disabled" and I do not know how to change this. I read that if two items fail to work correctly, then you have the wrong distro - is this my predicament or am I missing something really obvious?

There are times when particular menus and options require "administrator rights" to access them, I type in the same password that I used to log on and I'm returned to the menu but I still can't access the options. 

According to the KDE tutorial, the user should be able to see on their default desktop and in the panel, an icon with a house that indicates your home directory. I have neither of these and the tutorial also states that clicking on the desktop numbers in the panel will change your desktop, but I shuttle through them all and It's the same one! :confused: 

Sorry for the long post, if anyone can help put me back on track I'd really appreciate it as I'm not sure if It's something I've done to mess up the installation, an incompatibillity with KDE and my laptop or some blunder that I made somewhere. :-k 

Jay

---

### Post by trent dillman on 2006-04-15
The netgear card my need special drivers.

For the admin problems, reboot into recovery mode and do this:

```
echo '%admin   ALL=(ALL) ALL' >> /etc/sudoers
```

The Icon for Home should be there, don't know why it wouldn't be. And for the desktops, open some window on one, then switch and see if that works...

---

### Post by Jay Jay on 2006-04-15
Hi Trent, thanks for getting back to me.

The pointer about the multiple desktops worked like a charm, cheers :D 

I rebooted and tried the troubleshooting measure from the recovery mode console and it made no difference, when I returned to KDE the admin problem was still there. So rebooted and tried again, but still got no joy. As for the home icon, it is not on the desktop or panel and the only time I see is when I click onto "system" and it appears in a menu along with Wastebin, Settings etc.

I'm starting to suspect that something is very wrong, because apart from KsCD, none of the media players that are included will play ANY media, not even MP3's... ](*,) 

What do you suggest as my next move?

Jay

---

### Post by seoatway on 2006-04-16
To get most media players to work you need the right codecs, Automatix is a piece of software that sorts all that out for you. Find the thread on this forum which tells you all about installing and using automatix and it will sort out loads of stuff for you.

Cheers

BTW - I'm using wireless and KDE so if you are still stuck let me know and I'll see if I can help

---

### Post by Jay Jay on 2006-04-16
Alright thanks, I will download Automatix: I have to go back and forth to my Win machines in order to check for responses, download and burn software on CD and then return to the laptop. This impedes my progress, the ethernet port is disabled, so I can't hook the Omnibook up to my other boxes and just do a network transfer. 

> BTW - I'm using wireless and KDE so if you are still stuck let me know and I'll see if I can help

If it was possible to get my Netgear card working, then I could just go online straight from the Omnibook and obtain whatever software is required and browse and make changes from there directly. :) How do I go about this?

Jay

---

### Post by uteck on 2006-04-16
[QUOTE=Jay Jay]Hi, I'm a total novice to the Linux world. Up untill now my main experience has been with Windows and I'm trying to adjust to doing things differently now. :)  The other day I installed KDE 5.10 on my HP Omnibook 6000 laptop and so far I'm glad I made the switch, however there are few niggling issues that due to my lack of knowledge I am unable to resolve...

When I insert my Netgear WG511 v2 card, It's totally dead - KDE doesn't acknowledge It's presence, there are no lights on the card (I know that it works because I use it all the time with my Sony Vaio). My ethernet port is listed as "disabled" and I do not know how to change this. I read that if two items fail to work correctly, then you have the wrong distro - is this my predicament or am I missing something really obvious?

There are times when particular menus and options require "administrator rights" to access them, I type in the same password that I used to log on and I'm returned to the menu but I still can't access the options.

Jay[/QUOTE]
Just to spell it out to avoid any confusion;
When you use the System Settings and go to the Network Settings and click on Administrator Mode, enter your password, and when you click on the any line with an interface, the Configure Interface or Enable Interface buttons to not become active?

Did you have the card in the slot when you installed?  I had a problem a few years ago when I could only get wireless to work when the card was in the slot during install.  But I also knew less then, or things have just gotten easier.

Another option is to open Adept and search for 'wireless' and make sure you have all the various wireless tools installed.  If not, you can install them off the install disk.

---

### Post by Jay Jay on 2006-04-16
> Just to spell it out to avoid any confusion;
When you use the System Settings and go to the Network Settings and click on Administrator Mode, enter your password, and when you click on the any line with an interface, the Configure Interface or Enable Interface buttons to not become active?

That's correct, they're all grayed out and I can only see the option for administrator mode on network settings when I go: System>Settings>Network Settings. If I go via K Menu>System Settings>Network Settings, then administrator mode does not appear, at all.

> Did you have the card in the slot when you installed? I had a problem a few years ago when I could only get wireless to work when the card was in the slot during install. But I also knew less then, or things have just gotten easier.

No, I did not - it was in use on my other laptop at the time and I had no idea that the card would have to be present during the installation in order to be recognised.

> Another option is to open Adept and search for 'wireless' and make sure you have all the various wireless tools installed. If not, you can install them off the install disk.

You're going to have to show me how as I wouldn't have a clue how to do this... :oops: I tried to use Adept to install Xine so I could at least listen to some MP3's and failed...

---


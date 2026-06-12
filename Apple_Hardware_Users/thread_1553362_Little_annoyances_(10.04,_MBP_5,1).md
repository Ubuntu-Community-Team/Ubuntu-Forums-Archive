---
title: "Little annoyances (10.04, MBP 5,1)"
date: 2010-08-14
forum: Apple Hardware Users
---

### Post by HistoryMac on 2010-08-14
Hiya all! :D

I recently got around to installing Lucid Lynx on my 2009 MacBook Pro, which I use as my primary machine for work, school and media. Lucid Lynx is awesome, and I'm really happy to have it back as my primary OS, but there are a few little things that are giving me trouble.

:confused: Battery Life:
Under OS X (10.6.4) I get an average of about 3-4 hours of battery life. Ubuntu somehow manages to eat that up in about 45 minutes with minimal use (web browsing, a little text editing) so I'm forced to run off AC almost constantly. I have my processor (2.4GHz C2D) running at just 1.6GHz and on "Powersave" mode. 
Powertop returns: ```
 Power usage (ACPI estimate): 21.6W (0.4 hours) 
```

:D IBus **[SOLVED]**
[COLOR="Wheat"]As well as English, I also regularly type in Japanese. I have set up Romaji input in IBus, but have to start the daemon myself every time I reboot just to get the keyboard icon to show in the notification area. Ideally, I would like to have the daemon start automatically at boot-up, which I imagine isn't too difficult.[/COLOR]
**_[COLOR="DarkGreen"]-> SOLUTION: System > Preferences > Startup Applications. Click "Add" and enter "iBus" for name and "/usr/bin/ibus-daemon -d" as the command.[/COLOR]_**

:confused: Multiple keyboard layout options
Keyboard preferences adds a standard "USA" option everytime I reboot, despite me only needing (and wanting) the single "USA (Macintosh)" option there. Any way to stop it?

:D Gwibber auto-login **[SOLVED]**
[COLOR="Wheat"]Whenever I boot-up, I have to manually launch Empathy so that Gwibber will display me as "online". Anyway to get this to happen by itself without Empathy having to open (in the foreground, at least)?[/COLOR]
_**[COLOR="DarkGreen"]-> SOLUTION: System > Preferences > Startup Applications. Click "Add" and enter "Empathy" for name and "empathy" as the command. Empathy will log you in automatically in the background, no open window at boot.[/COLOR]**_

:D Trackpad **[SOLVED]**
[COLOR="Wheat"]I find the stock trackpad driver for the MBP very frustrating, as I am used to using two fingers while doing certain things (e.g. dragging a file on the desktop to another place) but as soon as I place two fingers on the trackpad, it either stops recognizing the input or jumps into scrolling mode.[/COLOR]
[COLOR="DarkGreen"]**-> SOLUTION: Follow instructions**[/COLOR] [**here**]("http://ubuntuforums.org/showthread.p...ght=multitouch")

---

### Post by dreamsburnred on 2010-08-15
1. Battery life: At the top panel right click and add system monitor and cpu freq scale. It shows you usage. It could also be a worn out battery.

2. Gwibber in options/admin click on preferred applications/startup applications. Click add and type in empathy in the first two boxes (name and app).

3. Ubuntu does not have multi-touch...at least that I am aware of. 

Hope that helps :popcorn:.

---

### Post by HistoryMac on 2010-08-15
> **dreamsburnred said:**
> 1. Battery life: At the top panel right click and add system monitor and cpu freq scale. It shows you usage. It could also be a worn out battery.

It's definitely not a worn out battery, as it performs fine under OS X, and my CPU usage is minimal so that's not it either.

> **dreamsburnred said:**
> 2. Gwibber in options/admin click on preferred applications/startup applications. Click add and type in empathy in the first two boxes (name and app).

I assume this means an empathy window will open at boot? Is there any way to have empathy start in the background?

> **dreamsburnred said:**
> 3. Ubuntu does not have multi-touch...at least that I am aware of. 

That's what I figured, bummer. Guess I'll have to make do with a mouse :( Thanks for your help though! :)

---

### Post by dreamsburnred on 2010-08-15
Yes empathy will open at boot.

Battery life is a mystery. :confused:

---

### Post by linuxopjemac on 2010-08-15
There is an experimental multitouch driver:
[http://ubuntuforums.org/showthread.php?t=1334696&highlight=multitouch](http://ubuntuforums.org/showthread.php?t=1334696&highlight=multitouch)

---

### Post by HistoryMac on 2010-08-15
> **linuxopjemac said:**
> There is an experimental multitouch driver:
[http://ubuntuforums.org/showthread.php?t=1334696&highlight=multitouch](http://ubuntuforums.org/showthread.php?t=1334696&highlight=multitouch)

Oh, great! :D Thanks, I'll go grab that now.

---

### Post by HistoryMac on 2010-08-15
Installed the Multi-Touch driver, and no my touchpad does nothing at all >_<
I think I may have done something wrong, I'll go through the steps again tomorrow and check. Thanks anyway :D

---

### Post by Nick_Jinn on 2010-08-15
I get great battery life with Linux Mint main edition. That is indeed a mystery.

Are you using more ram in Ubuntu? How much eye candy do you have enabled?

---

### Post by HistoryMac on 2010-08-15
> **Nick_Jinn said:**
> 
Are you using more ram in Ubuntu? How much eye candy do you have enabled?

No, actually. I'm using LESS! In OS X I had all 4GB, but I didn't have a copy of Ubuntu (64bit) on me, so I just used the 32bit version and am limited to 2.7GiB (I believe).

Eye Candy is pretty minimal. Other than the stock minimize, open, close and wobbly windows effects, I have nothing enabled.
This is really confusing me! :confused:
The last laptop I had Ubuntu on (a Toshiba Satellite) had greatly improved battery life under Ubuntu, as have all the other portables I have ever put it on... What's going wrong here?

---

### Post by HistoryMac on 2010-08-15
Just messed around with my trackpad setup and managed to get the multitouch driver working. It's still a little buggy, but a heck of a lot better than the stock one. Thanks for that linuxopjemac! :D

---

### Post by HistoryMac on 2010-08-17
Not sure how long this is going to last, but my battery suddenly seems to be last for a period of time significantly closer (1 hour 45 mins) to what it was getting under OS X. Nothing seems to have changed, so I have no idea what has caused this sudden improvement... 

Whatever it was, I'd like to happen a few more times; then my battery life might be back up to what I'm used to. :lolflag:

---

### Post by davidryderuk on 2010-08-17
Hi,
From what I've read in this forum, your computer has two graphics cards, a high powered nvidia geforce 9600M GT card and a low powered nvidia geforce 9400M card. Whilst OS X can switch between the two cards in order to balance performance and battery life, a couple of people report that Ubuntu can only see (and hence use) the high powered 9600M GT card.

[http://ubuntuforums.org/showthread.php?t=1127201](http://ubuntuforums.org/showthread.php?t=1127201)

[http://support.apple.com/kb/SP499](http://support.apple.com/kb/SP499)

The upshot of this is that Ubuntu probably wastes much more power on graphics than OS X. Because of this you'll probably never have quite as good battery life in Ubuntu, however **the fix below might improve the situation slightly.**

[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid#Set%20Graphics%20Card%20to%20Powersave%20Mode](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid#Set%20Graphics%20Card%20to%20Powersave%20Mode)

---

### Post by Linux_Youth******* on 2010-08-17
Do what I did when I was having Ubuntu issues and switch to another Linux. I'm using Mepis right now. Perhaps that'll do the trick. Or Linux Mint (as another poster commented on). I hope you find some from of solution to this issue though, regardless of the distribution you choose in the end.

Mepis: [http://www.mepis.org/](http://www.mepis.org/)
Mint: [http://linuxmint.com/](http://linuxmint.com/)

---

### Post by HistoryMac on 2010-08-20
> **davidryderuk said:**
> 
The upshot of this is that Ubuntu probably wastes much more power on graphics than OS X. Because of this you'll probably never have quite as good battery life in Ubuntu, however the fix below might improve the situation slightly.

I fear you may be correct... I think I'm going to go have to go out and get a new laptop anyway. As much as I love my MBP it's a bit too heavy to carry all around town everyday in my bag :P Thanks for your help though!

---


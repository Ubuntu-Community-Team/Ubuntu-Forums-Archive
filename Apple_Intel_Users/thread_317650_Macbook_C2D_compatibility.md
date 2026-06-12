---
title: "Macbook C2D compatibility"
date: 2006-12-12
forum: Apple Intel Users
---

### Post by avalonpimp on 2006-12-12
This post is about how compatible the new Macbook Core 2 duo, (non-pro) are with ubuntu Edgy, and also Drapper(under native install not parellels). And sources to fix problems. For those with this setup i have some questions...

1.How hot does it get, its a big concern of mine??
(under normal operation and heavy load..can you use it on your lap)

2. How long is the battery life under Ubuntu? (normal use)

3. What doesn't work out of the box in Edgy??

( [https://wiki.ubuntu.com/LaptopTestingTeam/AppleMacBookBlack](https://wiki.ubuntu.com/LaptopTestingTeam/AppleMacBookBlack) )
 - Is all this true? or is this outdated?

4. XGL/Beryl Experience postive and negative?

---

### Post by samden on 2006-12-13
Just a point - the new MacBooks use Intel chips, not PPC chips. Although you might find lots of interest from the Mac fans here, technically the MacBook should run the x86 version of Ubuntu, and the support in that section of the forum may be more relevant.

---

### Post by avalonpimp on 2006-12-14
gotcha, thx

---

### Post by handylinux on 2006-12-14
[QUOTE]1.How hot does it get, its a big concern of mine??[QUOTE]
New model is a little cooler than previous; see [Macworld article]("http://www.macworld.com/2006/11/firstlooks/mbtemps/index.php").

New (or revised) model is also a little faster than previous, otherwise little changed; see [Macworld review]("http://www.macworld.com/2006/11/reviews/13inmacbookcore2/index.php"). So the cited Ubuntu Laptop Test is probably all still valid.

---

### Post by kaiwondergoo on 2006-12-15
[COLOR="Navy"]Being the proud owner of a (not really) shiny new black macbook 2.0ghz, lemme see if I can help.[/COLOR]

[I]1.How hot does it get, its a big concern of mine??
(under normal operation and heavy load..can you use it on your lap)[/I]

[COLOR="Navy"]using OSX: eh, it gets warm - not enough to take out of my lap playing WoW for 20 min to really get it going.
using ubuntu: donno, about to redo it, looking for info myself. worried about the screen brightness*[/COLOR]

*2. How long is the battery life under Ubuntu? (normal use)*

[COLOR="Navy"]under OSX its doing very good. i wanted this as a wireless terminal more than anything and the battery life is much more important than speed. i have not been disappointed.
under ubuntu - donno yet, but i'll let you know my findings tonight or so once i test it
[/COLOR]

[I]3. What doesn't work out of the box in Edgy??
[/I]
[COLOR="Navy"]ummm wireless on the new macbook needs to use the ndiswrapper. not my favorite option, but there it is. the screen was overly bright after install and the video playback was... less than desirable... but i decided to reboot to OSX while i research the brightness issues. everything else seems fine so far (sound, screen res came up right, trackpad worked, etc). havent tested USB/Firewire/video out. [/COLOR]


[I]( [https://wiki.ubuntu.com/LaptopTestingTeam/AppleMacBookBlack](https://wiki.ubuntu.com/LaptopTestingTeam/AppleMacBookBlack) )
 - Is all this true? or is this outdated?
[/I]
[COLOR="Navy"]i'd have to start with outdated since my screen res was 1280x800 or whatever that native res is. but i am pretty sure that 915res was the reason
[/COLOR]
*4. XGL/Beryl Experience postive and negative?[/QUOTE]*

[COLOR="Navy"]i'll get to the fancy stuff when the system is installed and running propper. 

--
kwg

* the screen brightness is the only thing right off that concerned me. just worried about damaging it.

[/COLOR]

---

### Post by avalonpimp on 2006-12-16
awesome, keep the macbook/ubuntu world posted

---

### Post by kaiwondergoo on 2006-12-16
[COLOR="Navy"]uggg! ok round 2 was a complete failure. i attempted to just 'erase entire disk' and install. well, everything worked except the wifi. then it was too late to mess with and before i knew it i was sticking the restore dvd in and starting on round 3. thankfully it's saturday.

ya, so i found a [link]("https://help.ubuntu.com/community/MacBook")  that i'm using now, 915res was installed, there's a link to a backlight util there. i will return with the wifi news.

--
kwg

edit: oh ya, i was also using a linux mint livecd. i've gone back to the standard livecd for troubleshooting. [/COLOR]

---

### Post by avalonpimp on 2006-12-17
hopes these help u....

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
 - community wiki on macbook install

[http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)
 - very complete

[http://www.jasonparekh.com/linux-on-macbook/#vmware](http://www.jasonparekh.com/linux-on-macbook/#vmware)
 - nice install guide

[http://bin-false.org/?p=17](http://bin-false.org/?p=17)
 - another install walkthrough

[http://ubuntuforums.org/showthread.php?t=225621](http://ubuntuforums.org/showthread.php?t=225621)
 - getting isight to wrk

[http://www.ubuntuforums.org/showthread.php?t=304378&highlight=macbook+brightness](http://www.ubuntuforums.org/showthread.php?t=304378&highlight=macbook+brightness)
 - sleep mode information, and 6.10 compatibility / brightness

[http://www.ubuntuforums.org/showthread.php?t=198453&highlight=macbook+brightness](http://www.ubuntuforums.org/showthread.php?t=198453&highlight=macbook+brightness)
 - good MBP install, could help with Macbook C2D

[http://ubuntuforums.org/showthread.php?t=293061&highlight=macbook+remote](http://ubuntuforums.org/showthread.php?t=293061&highlight=macbook+remote)
 - macbook remote

[http://www.linux-on-laptops.com/apple.html](http://www.linux-on-laptops.com/apple.html)
 - has 4 install guides, one un-english, one repeat from previous link, and two gentoo (which are very complete)

[http://www.ubuntuforums.org/showthread.php?t=215801&highlight=macbook+brightness](http://www.ubuntuforums.org/showthread.php?t=215801&highlight=macbook+brightness)
 - control brightness

 hope this helps all

---


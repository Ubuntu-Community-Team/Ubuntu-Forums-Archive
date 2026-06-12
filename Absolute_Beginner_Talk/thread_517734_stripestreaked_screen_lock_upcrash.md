---
title: "stripe/streaked screen lock up/crash"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by justins1983 on 2007-08-04
'm using kubuntu 7.04, tried same version of ubuntu and i experience the same problem. the screen either goes completely white or has stripes or streaks the same colors as were just showing before the crash. i have to hard reboot and occasionally my cursor will then show as a blurred block at the log in screen. if i hit control + sys + backspace and then reboot it goes away. this crash occurs regularly, sometimes within a few minutes, most times several hours and occasionally a few days. it never happens when im away from the computer and almost always occurs when im using firefox although sometimes it will do it when another program is being used. it seems to me like my integrated video card(VIA K8M890 chipset) might be the problem, locking up if it cant handle frequent changes on the screen. however videos work just fine at full screen, can run for hours and wont lock up or hesitate. im a complete noob with linux so im hoping this system log is relevant and can help figure out whats going on

> 08/04/2007 08:01:20 PM	justin-room	kernel	[   46.784000] Time: acpi_pm clocksource has been installed.

08/04/2007 08:01:20 PM	justin-room	ntpdate[5223]	step time server 82.211.81.145 offset 14404.122649 sec

08/04/2007 08:01:21 PM	justin-room	avahi-daemon[4782]	Registering new address record for fe80::219:dbff:fe5d:a449 on eth0.*.

08/04/2007 08:01:23 PM	justin-room	kdm_greet[5227]	Can't open default user face

08/04/2007 08:01:29 PM	justin-room	kdm[5115]	X server for display :0 terminated unexpectedly

08/04/2007 08:01:29 PM	justin-room	kdm_greet[5227]	Internal error: memory corruption detected

08/04/2007 08:01:30 PM	justin-room	kernel	[   56.452000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.

08/04/2007 08:01:30 PM	justin-room	kernel	[   56.452000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode

08/04/2007 08:01:30 PM	justin-room	kernel	[   56.452000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

08/04/2007 08:01:30 PM	justin-room	kernel	[   56.780000] eth0: no IPv6 routers present

08/04/2007 08:01:32 PM	justin-room	kdm_greet[5240]	Can't open default user face

08/04/2007 08:01:36 PM	justin-room	init	tty1 main process (4262) killed by TERM signal

08/04/2007 08:01:36 PM	justin-room	init	tty2 main process (4260) killed by TERM signal

08/04/2007 08:01:36 PM	justin-room	init	tty3 main process (4261) killed by TERM signal

08/04/2007 08:01:36 PM	justin-room	init	tty4 main process (4256) killed by TERM signal

08/04/2007 08:01:36 PM	justin-room	init	tty5 main process (4257) killed by TERM signal

08/04/2007 08:01:36 PM	justin-room	init	tty6 main process (4263) killed by TERM signal

08/04/2007 08:02:54 PM	justin-room	kdm_greet[5295]	Can't open default user face

08/04/2007 08:02:54 PM	justin-room	ntpdate[5316]	step time server 82.211.81.145 offset 14404.121998 sec

08/04/2007 08:03:01 PM	justin-room	kdm_greet[5295]	Internal error: memory corruption detected

08/04/2007 08:03:02 PM	justin-room	kernel	[   56.040000] eth0: no IPv6 routers present

08/04/2007 08:03:27 PM	justin-room	hcid[5062]	Default passkey agent (:1.10, /org/bluez/passkey_agent_5485) registered

08/04/2007 08:03:54 PM	justin-room	gconfd (justin-5537)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

08/04/2007 08:03:54 PM	justin-room	gconfd (justin-5537)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0

08/04/2007 08:03:54 PM	justin-room	gconfd (justin-5537)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3

08/04/2007 08:03:54 PM	justin-room	gconfd (justin-5537)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

08/04/2007 08:03:54 PM	justin-room	gconfd (justin-5537)	Resolved address "xml:readwrite:/home/justin/.gconf" to a writable configuration source at position 1

08/04/2007 08:03:54 PM	justin-room	gconfd (justin-5537)	starting (version 2.18.0.1), pid 5537 user 'justin'


my computer actually locked up when i went to preview my post so heres the system log from that

> 08/04/2007 10:42:26 PM	justin-room	kdm_greet[5306]	Can't open default user face

08/04/2007 10:42:26 PM	justin-room	ntpdate[5327]	step time server 82.211.81.145 offset 14404.206799 sec

08/04/2007 10:42:34 PM	justin-room	kernel	[   55.944000] eth0: no IPv6 routers present

08/04/2007 10:52:07 PM	justin-room	kdm_greet[5306]	Internal error: memory corruption detected

08/04/2007 10:52:27 PM	justin-room	hcid[5079]	Default passkey agent (:1.10, /org/bluez/passkey_agent_5494) registered

08/04/2007 10:52:46 PM	justin-room	gconfd (justin-5536)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

08/04/2007 10:52:46 PM	justin-room	gconfd (justin-5536)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0

08/04/2007 10:52:46 PM	justin-room	gconfd (justin-5536)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3

08/04/2007 10:52:46 PM	justin-room	gconfd (justin-5536)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

08/04/2007 10:52:46 PM	justin-room	gconfd (justin-5536)	Resolved address "xml:readwrite:/home/justin/.gconf" to a writable configuration source at position 1

08/04/2007 10:52:46 PM	justin-room	gconfd (justin-5536)	starting (version 2.18.0.1), pid 5536 user 'justin'



anyone know what i can do to prevent these? very annoying!!

---

### Post by nitro_n2o on 2007-08-05
this is interesting ```
08/04/2007 10:52:07 PM justin-room kdm_greet[5306] Internal error: memory corruption detected 

```
Have installed any software lately (i don't use kde maybe kdm_greet is a program)

---

### Post by justins1983 on 2007-08-05
im just getting the hang of this OS, installed about a month ago. so ive installed a lot of software in the last month once ive learned whats available, what i need, how to install it, etc. however this problem existed since day one. it even did it when i was just running off of the live cd. im not aware of any program called kdm_greet. i also found the memory corruption to be interesting (disturbing more like it lol) but the memory test from the grub menu said i passed with zero errors. i just wish i could figure this out and get it fixed :confused:::(

---

### Post by nitro_n2o on 2007-08-05
this memory corruption is caused by some program.. it's not that you memory is not working anymore.. 
have u installed any plugins for firefox lately (since it happens when u use firefox)

---

### Post by justins1983 on 2007-08-05
yes i have installed plugs in for firefox recently. the crash happened before this though, even when using the live cd for ubuntu and kubuntu where i had no software installed. its happened when using the konqueror browser as well as other programs (ktorrent, adobe pdf files, maximized pidgin chat windows) . it just happens most frequently when using firefox. i believe this is because A) its the program i use most frequently at full screen and B) it seems to happen when going between tabs quickly, scrolling a page too fast or a new page quickly rendering. if i make a habit out of scrolling slowly and in increments and quickly minimize the browser after clicking a link (before the new page can render) it seems to avoid crashing as frequently.

---

### Post by justins1983 on 2007-08-05
anyone have an idea?

---

### Post by justins1983 on 2007-08-05
so after some googling it appears kdm_greet is a process that runs at login? others seem to be having problems with it but not the same problem as i am having. anyone have a suggestion as to what i could try to fix this? in a google result i found someone who added his login to a user group and that seemed to help him, would that be a good place to start for me? if you need more info just let me know what and how to get it and ill be glad to post it.

---

### Post by asmoore82 on 2007-08-06
have you ran memtest from the Live CD ?

---

### Post by justins1983 on 2007-08-06
i have not, i ran it from grub after installation. does it make a difference running it off of the live cd rather than a hard drive installation?

---

### Post by asmoore82 on 2007-08-06
do you ever dig into the hardware?
If so, would you be able to tell me if you have 2 sticks of RAM or all on one?

---

### Post by justins1983 on 2007-08-06
im using two 500mb sticks of ddr running dual channel.

---

### Post by justins1983 on 2007-08-06
so no one has ever heard of a bug like this? any guesses as to what i might try here?

---

### Post by justins1983 on 2007-12-05
still looking for help for this problem. ive been watching my memory usage today and i wonder if anyone can tell me if this might be whats going wrong. the memory use is very high but nothing in swap. 
 [IMG]http://i41.photobucket.com/albums/e263/ruddermike123/memuse1.jpg[/IMG]
[IMG]http://i41.photobucket.com/albums/e263/ruddermike123/memuse2.jpg[/IMG]

:confused:

---

### Post by Toadmund on 2007-12-05
Anything like this?
[http://ubuntuforums.org/showthread.php?t=420888]("http://ubuntuforums.org/showthread.php?t=420888")

---

### Post by justins1983 on 2007-12-05
yes the screen looks very similar to that when it locks up. mostly white with vertical stripes consisting of many short horizontal lines. the colors vary, sometimes its all white, sometimes very colorful. it seems to use the colors of whatever was on the screen the moment it locked up (usually firefox as i mostly use this computer for web browsing).

---

### Post by Toadmund on 2007-12-05
Like the solution in the link suggests, try disabling the 'AMD cool 'n' quiet' in the BIOS.
I *think* it's under 'power management'

---

### Post by justins1983 on 2007-12-05
ok i disabled cool n quiet, hope this works! i should know within a couple hours, lately ive been having 5-6 lock ups a day. cross your fingers for me and thank you for the help. ill be sure to update in a couple of days if this does finally fix my problem! :)

---

### Post by Toadmund on 2007-12-10
Well...uhhhhhhhhh......?

So,.........Howjya make out? :-k

---

### Post by justins1983 on 2007-12-10
> **Toadmund said:**
> Well...uhhhhhhhhh......?

So,.........Howjya make out? :-k

no crashes! :) looks like that was indeed the fix ive been looking for. thanks for the help, wish i had found that thread months ago lol

---

### Post by Toadmund on 2007-12-10
Good :)
I put up with the same problem forever myself, when I finally stumbled upon something someone suggested on a bug report, it was one among other suggestions I tried.
It worked for me, and I am glad it worked for you!

---


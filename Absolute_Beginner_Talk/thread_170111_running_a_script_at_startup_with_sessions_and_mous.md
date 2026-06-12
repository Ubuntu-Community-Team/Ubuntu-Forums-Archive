---
title: "running a script at startup with sessions and mouse touchpad?"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-05-03
hey i have a script i need to run at startup.. to enable my ndiswrapper and wpa_supplicant

how can i run the script as root at startup.. in the sessions menu?

do i just do sudo /home/joshua/scripts/script.sh ?

can i make it so i dont have to put in my password


question #2 how can i disable the mouse touchpad click when you tap it
its messing me up when i tap the pad to move the cursor and it thinks i want to click something.. i didnt see it in the mouse preferences

---

### Post by FryerFox on 2006-05-04
To disable tap-clicks, try [http://scottcollins.net/blog/2006/01/disable-touchpad-tap-in-kubuntubreezy.html]("http://scottcollins.net/blog/2006/01/disable-touchpad-tap-in-kubuntubreezy.html") or [http://ubuntuforums.org/archive/index.php/t-27650.html]("http://ubuntuforums.org/archive/index.php/t-27650.html") (I used the second method).

---

### Post by jazzmuzik on 2006-05-04
I had the same question a while back. Create a file called /etc/init.d/local, give it execute permissions (755) and put your commands in there. Here's mine:

#! /bin/sh
echo 1024 > /proc/sys/dev/rtc/max-user-freq

THen you create links in the /etc/rc.* directories. See this page:

[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

---

### Post by nanotube on 2006-05-04
[QUOTE=joshrobinson]hey i have a script i need to run at startup.. to enable my ndiswrapper and wpa_supplicant

how can i run the script as root at startup.. in the sessions menu?

do i just do sudo /home/joshua/scripts/script.sh ?

can i make it so i dont have to put in my password


question #2 how can i disable the mouse touchpad click when you tap it
its messing me up when i tap the pad to move the cursor and it thinks i want to click something.. i didnt see it in the mouse preferences[/QUOTE]

for tap click - go to the first link in my sig, and find the "disable tap click" section.

for running a script as root... best way would be to follow jazzmuzik's instructions - put your script into ```
/etc/init.d/yourscriptname
```
then activate it, using the "update-rc.d" command, as follows:
```
sudo update-rc.d yourscriptname defaults
```
that should get you going.

---

### Post by joshrobinson on 2006-05-04
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "MaxTapTime"            "0"


thats my xorg.conf.. tap click is still on :-( maybe because im using dapper?

---

### Post by nanotube on 2006-05-04
did you restart x? or even better, reboot?

---

### Post by joshrobinson on 2006-05-04
[QUOTE=nanotube]did you restart x? or even better, reboot?[/QUOTE]

yeah i rebooted multiple times, changing options here and there i saw on other websites.. im guessing it has to be a bug with dapper drake, because from what ive read that you guys posted it seems to work for breezy](*,)

---

### Post by nanotube on 2006-05-04
[QUOTE=joshrobinson]yeah i rebooted multiple times, changing options here and there i saw on other websites.. im guessing it has to be a bug with dapper drake, because from what ive read that you guys posted it seems to work for breezy](*,)[/QUOTE]
yea, it worked for me just like that, so i don't know what else to suggest. try posting this in the dapper drake forum, and see if anyone knows why it doesn't work.

---

### Post by joshrobinson on 2006-05-04
[QUOTE=nanotube]yea, it worked for me just like that, so i don't know what else to suggest. try posting this in the dapper drake forum, and see if anyone knows why it doesn't work.[/QUOTE]

will do tomarrow.. thanks for the commands for the startup script.. worked great :D

---


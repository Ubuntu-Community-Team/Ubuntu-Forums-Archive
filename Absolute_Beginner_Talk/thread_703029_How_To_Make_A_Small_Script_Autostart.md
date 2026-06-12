---
title: "How To Make A Small Script Autostart?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-02-20
Hello all.  I've been using Gutsy for about a week now, and without this forum, I would have been totally lost.  Many thanks for the great advice, and the sharing of knowledge and experience!

I have done a search, but have not found a suitable answer for the problem I have.  I want to be able to shut the LCD off after 2 minutes of inactivity.  I have come up with this very small script:

#!/bin/sh
xset dpms 0 0 120



I then saved that script to /usr/bin/Blanker, and used this command:
sudo chmod +x /usr/bin/Blanker


Now, after startup of the system, if I run it in a Terminal like this:  /usr/bin/Blanker     it works just fine, and totally turns off all power to the LCD after 2 mins of no activity.


OK, good so far.  My problem is trying to get it to work automatically at startup.   I have tried to add it to the System -  Prefs - Sessions    with the same command of /usr/bin/Blanker  , then did a reboot, but it did not work.    

So, reading the threads on this forum, I tried the following:

I added  xset dpms 0 0 120      to the end of the file   /etc/int.d/reS.sh       

Actually, my command was the only thing in that file, I suppose it did not exist before I made it with the command sudo gedit /etc/int.d/reS.sh .    Anyways, I did another reboot, and that did not work either.


Would someone please teach me how to do this?  If I can learn this simple task, then I can use the experience to do more things down the road.

Thanks much!  

FreewareFan

---

### Post by spiderbatdad on 2008-02-20
I believe chmod 755 your file and just put it in /etc/init.d

---

### Post by mattismyname on 2008-02-20
Put it in the start section in /etc/init.d/rc.local

---

### Post by Origin415 on 2008-02-20
Make sure your user has permissions -- if you are using it without sudo, its not the problem, but just to be sure.

You could also try adding it to /etc/rc.local

But doesnt Gnome already have a power manager function to do this? (though that isnt a very satisfying solution if you are trying to learn)

---

### Post by FreewareFan on 2008-02-21
Thanks for the quick suggestions!

@spiderbatdad  I tried your suggestion, but when I rebooted, it did not work.  I appreciate you taking the time to offer the idea, tho!

@mattismyname and Origin415   I have tried to do what you both suggested a couple of different ways.   No results yet.  It's probably because I don't know exactly where to insert that line of command.  Here is my latest try, maybe you could tell me the correct way to do the file??  

```
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
xset dpms 0 0 120
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

The reason I'm doing this, Origin415 is because thru the Screensaver setting there is a way to blank the screen, but what really happens is that the screen is just painted black.  There is still power going to the backlight, and it still can drain the battery if I'm on battery power with my laptop.   Using xset dpms 0 0 120   actually turns off the power to the backlight and LCD.   So, that's why I'd like to get this to work.

In the meantime, I've made a desktop launcher that makes a call to the Blanker script I made, and it works just fine if I click it.   I would just really like to learn how to make this a automatic thing everytime Gutsy boots.

Thanks again for any suggestions coming this way!!

FreewareFan

---

### Post by FreewareFan on 2008-02-21
Would anyone else have any idea how I can do this?  I would greatly appreciate the help.

FreewareFan

---

### Post by Trail on 2008-02-21
Placing that line on /etc/init.d/rc.local (before the return 0, without sudo) should work.

By the way, KDE has an ability to automatically execute scripts, individually for each user just after logging in, by using the contents of the folder ~/.kde/Autostart.

I am sure GNOME would have something similar, but I don't know of any at the moment.

---

### Post by rfurman24 on 2008-02-21
Just go to System- Preferences- Sessions and add /usr/bin/Blanker. Now control+alt+backspace and log back in. It should auto start.

---

### Post by FreewareFan on 2008-02-21
Well, thanks everyone for the suggestions, but I give up on it, for now.  I tried all things suggested, and even more, but the thing still will not autorun no matter what I do.

Guess it's best if I wait a few months to give myself some time with Gutsy, then when I know more, I'll attack the project again.

Later!

FreewareFan

---

### Post by jordanmthomas on 2008-02-21
Just so you know, putting it in /etc/rc.local won't work if X isn't startedyet (I'm guessing it probably is when /etc/rc.local gets run, but I don't know if gdm gets backgrounded or how it works in Ubuntu).

You could try changing your script to this:
```
#!/bin/bash
DISPLAY=:0.0 xset dpms 0 0 120
```

Also, you can configure X to do this without needing to use xset (this is probably a better solution than your script).
A post I made on the matter in the past:
[http://ubuntuforums.org/showpost.php?p=4283283&postcount=2](http://ubuntuforums.org/showpost.php?p=4283283&postcount=2)
Instead of 20 here, you would want to use 2.


Hope this helps.

---

### Post by FreewareFan on 2008-02-22
Well, I read your post twice, and did what you instructed.  I rebooted, and nothing...  This is a real bummer, because I'm thinking that one of these suggested methods should have worked, but so far, I'm batting zero...

Here is the code after I changed it:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        Option          "Offtime"           "2"

```

As far as I can tell, I did exactly what you told me to do, but it still doesn't work.  Any idea what I could be doing wrong??   Thanks for your efforts on this!

FreewareFan

---

### Post by jordanmthomas on 2008-02-22
That *should* have worked.  The only thing I can think of now is that perhaps the gnome-power-manager is changing the setting.  Look at System -- Preferences -- Power Management and see if anything in there helps.  I don't use gnome and when I do I don't use its power manager, so I've never had this problem.

Also, if worse comes to worse you can add your script to the gnome session manager (system -- preferences -- sessions) and it'll be run when you log on.

---

### Post by samkline on 2008-02-22
Go to the terminal and type
[FONT="Courier New"]sudo gedit /etc/X11/xinit/xinitrc[/FONT]
At the end of that file, you can put your command
[FONT="Courier New"]xset dpms 0 0 120[/FONT]
Then restart X by logging out. When X starts (you see the login screen), it should run that command.

---

### Post by FreewareFan on 2008-02-23
@jordanmthomas   There's nothing in the power managment settings that I could tell would stop this script being run at startup...  And as for using the sessions manager, I did that a long time ago, as I included in my very first post..  

@ samkline  I did what you suggested, and when I got back into the system, I waited two minutes and more, but nothing....   This is really strange, to have tried everyone's suggestion, and not one of them work.  I'm almost starting to feel like I have a small gremlin in this system.....  or is it a small Gnome?  ha


Thanks to you both for your suggestions!!

---

### Post by jordanmthomas on 2008-02-23
Hm, if you still have your xorg.conf edited to have the DPMS stuff in there, what happens if you leave it on the login screen for two minutes?
If it works here, then there is obviously *something* changing the offtime when you are logging in to gnome.  My first guess is the gnome-power-manager and its blanktime setting (see attachment).  

It could also be your screensaver.  Maybe you could try switching to xscreensaver instead of gnome-screensaver.  Not only will you actually be able to have options for your screensavers (hours of fun), you'll be able to edit more options pertaining to the screen's power.  (Really, using gnome-screensaver is one of the worst choices the Ubuntu team has ever made)

I'm like you and like to turn off my screen whenever possible, which is why I just forgo screensavers altogether.  

I really think your problem will be solved if you use xscreensaver instead of gnome-screensaver, without the need for the script (or maybe the script would actually work for once since nothing will be changing the offtime)

Finally, as a last thing just for fun:
```
xset -display :0 dpms force off
```
You can run this whenever you want to turn the screen off.  I bind it to the stop button on my laptop since I don't use that button anyway.

---

### Post by seventhc on 2008-02-23
can't you just put it the start up under sessions?? I have a script that starts that way.
I keep it in my home folder as a hidden file, to do this you would save it as .name.sh then
```

chmod +x .name.sh
chmod 755 .name.sh

```then go to
[I]System>Preferences>Sessions
Startup Programs
[/I]click on *Add*
then for the command put
*[COLOR=DarkRed] /home/your_username/.name.sh[/COLOR]*
Then it should start up.

---

### Post by jordanmthomas on 2008-02-23
He said it doesn't work that way.
(I didn't catch it in his post either :) )

---

### Post by seventhc on 2008-02-23
oh I didn't see that...but that has to work...if one script will start that way, then any script should start that way...and I have a start up script for my conky...:confused:

---

### Post by seventhc on 2008-02-23
just found this [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F)
this is what they say to do
They also say to make it executable but they didn't put the code in...but I thinks it's already been made executable anyway.
```

[FONT=monospace]sudo cp ~/Desktop/mybootscript /etc/init.d
sudo chmod 755 /etc/init.d/mybootscript
sudo update-rc.d mybootscript defaults 90
[/FONT]
```

---

### Post by FreewareFan on 2008-02-23
Thanks seventhc, but that did not work either.  I'm about ready to give up on this thing, until I learn more about ubuntu and how it works.   For now, I'll just keep using the desktop launcher I made for it.   I can live with that for the time being.....

---


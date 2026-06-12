---
title: "Few Problems"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Nigmah on 2007-07-24
[COLOR=DarkOrange][B]OK first thing is I was having problems whenever i logged into xgl having no restart or shutdown buttons i fixed this by changing my startxgl.sh

From 
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:razz:buffer -accel glx:razz:buffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

to:
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:razz:buffer -accel xv:razz:buffer &
sleep 4  
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session

except now all my buttons and such look like im running windows 98 or os 9 which is really annoying.

Also i've tried multiple times to get my side buttons on my intellimouse 2.0(yes i've had it for a long time) but i can't get it to work here my xorg.conf looks like for my mouse
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "Resolution"            "100"
EndSection

also soon i'm going to be buying and installing the 8800 gts on my computer anything i should know before i do that[/B][/COLOR]

---

### Post by Foxmike on 2007-07-24
Is there a good reason you are using XGL?  XGL is deprecated now that AIGLX is available... and AIGLX is a lot less resources-intensive than XGL.

---

### Post by Nigmah on 2007-07-26
[COLOR=DarkOrange]**I'm using xgl because i'm using the propriety drivers for my card(ati radeon xpress 200) becauser there aren't any free ones, can i still use aiglx with the proprietary driver?**[/COLOR]

---

### Post by bromix on 2007-07-26
I'd like to know too.  I have the same problem with those buttons missing when using XGL

---

### Post by bromix on 2007-07-26
Hey, check this post out.  It will help you.    [http://www.getautomatix.com/forum/index.php?showtopic=732](http://www.getautomatix.com/forum/index.php?showtopic=732)

---

### Post by bromix on 2007-07-26
In the terminal....type sudo gedit /usr/bin/startxgl     then add the RED items.   Don't change anything to look like his.    It worked awesome for me.   I liked the all black background that adding the -br gives me instead of that funky grey.

---

### Post by Foxmike on 2007-07-26
Beryl/Compiz should work fine with proprietary drivers, but not with all video cards.  Just make a look [here]("http://wiki.ubuntu.com/BerylOnFeisty") for a good guide on that topic.
 
Good luck!

---

### Post by Nigmah on 2007-07-26
[COLOR=DarkOrange]**Did you guys even read the first post?**[/COLOR]

---

### Post by Foxmike on 2007-07-27
> **Nigmah said:**
> **[COLOR=darkorange]except now all my buttons and such look like im running windows 98 or os 9 which is really annoying.[/COLOR]**
 
What does that mean?  It's been a looooong time since I have lastly ran win98 and I never ran OS9.
 
What do you want to know exactly?

---


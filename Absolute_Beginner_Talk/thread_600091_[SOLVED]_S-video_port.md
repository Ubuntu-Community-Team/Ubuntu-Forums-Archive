---
title: "[SOLVED] S-video port"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by wjsparks on 2007-11-01
I can't use my s-video port to connect to my TV. Is there another driver i have to download?
Thanks

---

### Post by defrex on 2007-11-01
What's your video card?

---

### Post by wjsparks on 2007-11-01
Mobility Radeon 9600 M10

---

### Post by seanf on 2007-11-04
I'm having the same problem - no display on S-video with a Radeon Mobility 9600.

Computer is Averatec 6128H laptop.

I'm using Gutsy, with the open source ati driver, not fglrx.

Following along at [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12) I've done the following:

```
$ xrandr --output S-video --set load_detection 1
$ xrandr --output S-video --set tv_standard ntsc
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1200
VGA-0 disconnected (normal left inverted right)
LVDS connected 1280x800+0+0 (normal left inverted right) 0mm x 0mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video connected 800x600+0+0 (normal left inverted right) 0mm x 0mm
   800x600        59.9*+   60.3
```

So, S-video output is detected.. and if I disconenct the cable and run xrandr again, it shows that S-video is disconnected.

But then, when I run:

```
$ xrandr --output S-video
```

I get nothing on the TV, except for 'No signal'.

My xorg.conf is attached - any ideas would be most appreciated.

---

### Post by Dr Small on 2007-11-04
Have you tried atitvout ?

---

### Post by seanf on 2007-11-04
no luck with atitvout..

```
$ sudo atitvout detect
CRT is attached.
TV is attached via S-Video.

$ sudo atitvout ntsc t
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!

$ sudo atitvout ntsc auto
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!
```

thinking atitvout just doesn't work with a 9600... anything else I could try?

(read here: [http://www.thinkwiki.org/wiki/Atitvout](http://www.thinkwiki.org/wiki/Atitvout) that atitvout doesn't work with xorg > 6.7)

---

### Post by seanf on 2007-11-04
**SOLVED!**

On a hunch, I removed my xorg.conf entirely (after making a backup, of course) and let xorg configure itself, and now s-video works after running the following commands:

```
xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --output S-video --auto
```

Everything looks fine on the TV, except the two displays are running as clones, so I'm only seeing part of the desktop on the TV (laptop LCD is 1280x800, s-vid is 800x600)

Will post back here when I work out how to get big-desktop mode running. :)

---

### Post by BrendanM on 2007-11-04
Sounds good. You should mark this thread [Solved] to help other people who have the same issue, too.

---

### Post by seanf on 2007-11-04
I don't quite know how to do that :/

---

### Post by BrendanM on 2007-11-04
It's under "Thread Tools" at the top of the forum. I think only the original poster (or maybe moderators?) can mark threads solved.

---

### Post by seanf on 2007-11-04
> **BrendanM said:**
> It's under "Thread Tools" at the top of the forum. I think only the original poster (or maybe moderators?) can mark threads solved.

That must be it, because I don't see it :)

Still stymied on how to get big-desktop working. I know I'm going to have to re-instate my xorg.conf file to get it working, just need to find the secret sauce to make it all work.

---

### Post by seanf on 2007-11-05
> **seanf said:**
> Still stymied on how to get big-desktop working. I know I'm going to have to re-instate my xorg.conf file to get it working, just need to find the secret sauce to make it all work.

Well, that was easier than I thought.... I put my original xorg.conf back into place, and added "Virtual" line in the screen section:

```
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
        [COLOR="Red"]**Virtual 2080 800**[/COLOR]
	EndSubSection
EndSection
```

The "2080 800" comes from the added width of my two displays (1280+800) and the maximum height of the two displays (800).

Rebooted the computer, then ran:

```
xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --output S-video --auto
xrandr --output S-video --left-of LVDS
```

Bingo - big-desktop with native 1280x800 resolution on the LCD, and 800x600 on s-video :)

I couldn't get videos to play fullscreen on the TV.... off to sort that one out now..

---

### Post by wjsparks on 2007-11-05
I can't seem to find my xorg.conf file.  I installed atitvout and was able to reproduce some of your results, but as of now i am still stuck.

---

### Post by seanf on 2007-11-05
> **wjsparks said:**
> I can't seem to find my xorg.conf file.  I installed atitvout and was able to reproduce some of your results, but as of now i am still stuck.

Huh? The results I got from atitvout were that atitvout doesn't work for a 9600. 

Your xorg.conf, if you have one, is in /etc/X11.

If you don't have one there, then just try the xrandr steps I mentioned [here]("http://ubuntuforums.org/showpost.php?p=3708537&postcount=12").

---

### Post by GrantB on 2007-11-09
I have a similar problem.  This thread was helpful, but my laptop is still not recognizing when I plug in the S-Video cable.  How can I get "disconnected" to be "connected"?

My thread:
[http://ubuntuforums.org/showthread.php?p=3740376](http://ubuntuforums.org/showthread.php?p=3740376)

---

### Post by seanf on 2007-11-09
> **GrantB said:**
> I have a similar problem.  This thread was helpful, but my laptop is still not recognizing when I plug in the S-Video cable.  How can I get "disconnected" to be "connected"?

My thread:
[http://ubuntuforums.org/showthread.php?p=3740376](http://ubuntuforums.org/showthread.php?p=3740376)

According to your xorg.conf, you're using the proprietary driver - my solution worked with the open source driver, not fglrx.

Have you tried the Catalyst GUI tool?

---

### Post by Furiattl on 2008-03-19
I'm gonna try this later on

---


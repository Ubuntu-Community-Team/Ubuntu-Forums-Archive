---
title: "Xubuntu Screen Blanking Problem"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by reset3x on 2007-10-30
When I installed Xubuntu 7.10 my screen goes blank when I turn off the screen savers. I tried installing gnome power management but it doesn't have any effect. I just want my monitor to stay on all of the time.... I had no problem with this in 7.04.

System SPECS:

Athlon 64 3200+
1 GB RAM
nVidia 8600 GT


 Any ideas?

---

### Post by aidanr on 2007-10-30
Add

```
Section "ServerFlags"
	Option		"blank time" "0"
	Option		"standby time" "0"
	Option		"suspend time" "0"
	Option		"off time" "0"
EndSection

```
to xorg.conf (sudo mousepad /etc/X11/xorg.conf) and restart X (ctrl+alt+backspace)

---

### Post by NT4usB on 2007-10-30
I don't have an answer, just curious... How did you stop it in 7.04?
I've gone so far as killing gnome-screensaver and gnome-power-mangler processes and my mythbox still goes blank after a while of inactivity...

---

### Post by Duck2006 on 2007-10-30
> **NT4usB said:**
> I don't have an answer, just curious... How did you stop it in 7.04?
I've gone so far as killing gnome-screensaver and gnome-power-mangler processes and my mythbox still goes blank after a while of inactivity...

Do you have a power saving in your BOIS turn on.

---

### Post by NT4usB on 2007-10-30
> **Duck2006 said:**
> Do you have a power saving in your BOIS turn on.

...don't know.
Great idea though. Gonna look at that.
It's an upgrade from 6.06 and it ran a year that way without blanking. Since I haven't touched the bios, I'd assume it's all the same.
Strange thing is, it will some times go many hours sitting on the mythmenu. 
Come home after work, turn on the TV (different remote) and it's awake.
Other times, TV comes on,[COLOR="Green"] composite[/COLOR] in the left corner of a black screen. Wakes right up though, when I press the myth remote.
Pause a show, sometimes it goes black in ~ 20 minutes. Other times it'll stay on for hours.

(sorry about the thread hijack, reset3x)

---

### Post by reset3x on 2007-10-30
> **aidanr said:**
> Add

```
Section "ServerFlags"
	Option		"blank time" "0"
	Option		"standby time" "0"
	Option		"suspend time" "0"
	Option		"off time" "0"
EndSection

```
to xorg.conf (sudo mousepad /etc/X11/xorg.conf) and restart X (ctrl+alt+backspace)

Just curious... I don't have this problem in my laptop... exact same setup and apps... :confused:

---

### Post by reset3x on 2007-10-30
> **Duck2006 said:**
> Do you have a power saving in your BOIS turn on.

I didn't touch my bios... Things were great with 7.04... :confused:

---

### Post by NT4usB on 2007-10-30
iirc, I've already added these to my xorg and it didn't help.

---

### Post by NT4usB on 2007-10-30
> **reset3x said:**
> I didn't touch my bios... Things were great with 7.04... :confused:

Just for fun, kill the gnome-screensaver and power-manager process and see if it still blanks.

ed: I see your a gamer. I need a standalone contract bridge game so I can cure my mom of her mac habit and get her using Linux. Any suggestions?

---

### Post by reset3x on 2007-10-30
> **NT4usB said:**
> Just for fun, kill the gnome-screensaver and power-manager process and see if it still blanks.

ed: I see your a gamer. I need a standalone contract bridge game so I can cure my mom of her mac habit and get her using Linux. Any suggestions?


[Linux Mint]("http://linuxmint.com/") .... My 70 year old mom uses it with little help from me.... But I see your mom uses MAC... Is it a PPC?

---

### Post by reset3x on 2007-10-30
> **NT4usB said:**
> ...don't know.
Great idea though. Gonna look at that.
It's an upgrade from 6.06 and it ran a year that way without blanking. Since I haven't touched the bios, I'd assume it's all the same.
Strange thing is, it will some times go many hours sitting on the mythmenu. 
Come home after work, turn on the TV (different remote) and it's awake.
Other times, TV comes on,[COLOR="Green"] composite[/COLOR] in the left corner of a black screen. Wakes right up though, when I press the myth remote.
Pause a show, sometimes it goes black in ~ 20 minutes. Other times it'll stay on for hours.

(sorry about the thread hijack, reset3x)

I could care less about hijacking as long as people get help....

Peace!!!

---

### Post by NT4usB on 2007-10-30
> **reset3x said:**
> [Linux Mint]("http://linuxmint.com/") .... My 70 year old mom uses it with little help from me.... But I see your mom uses MAC... Is it a PPC?
My dad has an old (G4?) she uses and she hates it.
I'm building her her own box, put some good sound on it (she sings at the local college and many of the pieces she learns are online) and blow that MAC away.
She has to have her Bridge game though. Been the only hurdle getting it going.
btw, She's also 70. Dads 73 and still racing his car on the [weekends]("http://www.vararacing.com/Overall1.html"). I hope I'm still vertical when I'm 70 *g*

---

### Post by reset3x on 2007-10-31
> **NT4usB said:**
> My dad has an old (G4?) she uses and she hates it.
I'm building her her own box, put some good sound on it (she sings at the local college and many of the pieces she learns are online) and blow that MAC away.
She has to have her Bridge game though. Been the only hurdle getting it going.
btw, She's also 70. Dads 73 and still racing his car on the [weekends]("http://www.vararacing.com/Overall1.html"). I hope I'm still vertical when I'm 70 *g*

Yoor G4 is PPC: See [Here]("http://www.debian.org/ports/powerpc/").

---

### Post by reset3x on 2007-11-01
> **aidanr said:**
> Add

```
Section "ServerFlags"
	Option		"blank time" "0"
	Option		"standby time" "0"
	Option		"suspend time" "0"
	Option		"off time" "0"
EndSection

```
to xorg.conf (sudo mousepad /etc/X11/xorg.conf) and restart X (ctrl+alt+backspace)

Don't work.... Bumpity Bump...

---

### Post by NT4usB on 2007-11-01
Tried this one a while back, didn't work for me either.
What's really annoying (for me, anyway) is gnome-screensaver (or, any other screensaver process I can recognize) and gnome-power-manager are not running! I killed them... and I still get a blank screen after 15 minutes or so.

---

### Post by newlinux on 2007-11-01
If you have it in your xorg.conf comment out:

Option "DPMS"

might help. Worked on two of my frontends...

---

### Post by reset3x on 2007-11-01
Doesn't appear in my Xorg.conf... :confused:

---

### Post by NT4usB on 2007-11-01
I have it in the Monitor section for the LCD in my dual monitor xorg. It's not in the Monitor section for the TV in the dual monitor xorg.
I don't think it's in my 'TV only' xorg... Have to check it tonight.

---

### Post by reset3x on 2007-11-03
Gave up... Tried all suggestions... Learning to live with it :confused:

---

### Post by Shinoda on 2007-11-03
> **aidanr said:**
> sudo mousepad /etc/X11/xorg.conf
[FONT=Courier New]gksudo[/FONT] is recommended for graphical apps.

---

### Post by NT4usB on 2007-11-04
> **reset3x said:**
> Gave up... Tried all suggestions... Learning to live with it :confused:
Well, I've concluded if I restart, and kill gnome-power-mangler and gnome-screensaver right away, I don't get blanking... at the menu level anyway. Remains to be seen if a paused program will blank.
Anyway, if I forget to kill those, and get reminded by a blank screen, killing them at that point doesn't stop the screen blanking.
Now, to figure out how to remove those processes from the start menu.

---

### Post by Ballena on 2007-11-07
This thread helpt me a lot! Thanks guys.

---

### Post by MadMarv on 2007-11-19
Just found this thread - I had the same problem after upgrading to Xubuntu Gutsy. Once I realized gnome-screensaver was now default, I thought having it running over xscreensaver was the issue so I uninstalled it completely. Then I reinstalled xscreensaver (just in case it was borked by the upgrade) and added it to the startup menu so it would load on boot. Have not had any unexpected blanking since.

---


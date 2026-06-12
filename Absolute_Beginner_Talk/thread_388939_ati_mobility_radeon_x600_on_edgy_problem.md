---
title: "ati mobility radeon x600 on edgy problem"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by augie on 2007-03-20
Hello All,

I've just turned into Edgy from W. XP and I adore it!:) Anyway, my problem is that instead of my real graphics card I get the following:
> OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)

instead of:

> Ati Mobility Radeon X600 256mb 

I tried to install the driver from ATI website but no success.

Do you guys think Beryl and similar will work on this card?

Yesterday, I installed beryl but the screen was just not in the proper resolution and beryl itself would not change anything. (In gnome the graphics looks just fine)

Thanks a lot for you help,

augie:confused:

---

### Post by Kobalt on 2007-03-20
Installing the proper drivers for your graphic card is described [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html").

Your card should be capable of runing Beryl, but it can be tricky on some ATI hardware. I suggest you run into installing Beryl only if you feel capable of restoring your system (possibly from the command line).

---

### Post by augie on 2007-03-20
Thanx a lot.

Actually, I tried this link before and everything went smoothly. I followed the instructions and there is still the thing that bothers me, namely the system shows:

OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)

and not my real card. Is this ok? Or should I do something about it?

Thank you,


augie

---

### Post by Kobalt on 2007-03-20
As long as your graphics and display are working smoothly, I wouldn't bother... What's your card labelled in xorg.conf ?
```
cat /etc/X11/xorg.conf
```

---

### Post by augie on 2007-03-20
Hi Kobalt,
It's labelled:

ATI Mobility Radeon X600

---

### Post by Kobalt on 2007-03-20
Well then it's just fine :) 
ATI must be using a third party manufacturer chip on its card or something like this...

---

### Post by david_kt on 2007-03-20
Check this:

[INDENT]glxinfo | grep render[/INDENT]

in terminal. What is the output?

DK

---

### Post by augie on 2007-03-20
> **david_kt said:**
> Check this:

[INDENT]glxinfo | grep render[/INDENT]

in terminal. What is the output?

DK

The output:

> direct rendering: Yes

I guess that's fine, but still I installed Beryl and it wouldnt work, has it got anything to do with the ATI or just my beryll installation went not ok?

Cheers,

augie

---

### Post by Kobalt on 2007-03-20
It's both your beryl install & ATI related, these graphic cards are sometimes tricky to get going in Linux (ATI being the responsible because non cooperating part). 
What method did you use to install Beryl ?

---

### Post by augie on 2007-03-20
I tried the step-by-step from [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")

---

### Post by Kobalt on 2007-03-20
Why not trying to use AIGLX instead of XGL ? 
Didn't you notice their note at the begining of the HowTo > Note: Using AIGLX is preferred on Edgy Eft because it is included with X.org on Edgy

That is good advice, I would suggest you to use AIGLX instead of XGL at first.
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

---

### Post by augie on 2007-03-20
> **Kobalt said:**
> Why not trying to use AIGLX instead of XGL ? 
Didn't you notice their note at the begining of the HowTo 

That is good advice, I would suggest you to use AIGLX instead of XGL at first.
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

Holly Molly, I didnt notice that at all!

Thanx,

I hope it works this time.

augie

---


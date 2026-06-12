---
title: "GNOME and Monitor settings"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by oomingmak on 2007-04-06
Why is it that there is not one single widescreen setting in the Gnome applet that sets display resolution?

All the options provided seem to be 4:3 (and as a result my desktop and icons etc. are all horribly stretched out horizontally).

Surely the Gnome developers must have heard that 16:9 and 16:10 monitors exist and are common place these days.

I've given up trying to get the drivers installed for my graphic card on Ubuntu, and so if only I could get the correct aspect ratio to work then I'd live with the appallingly slow Ubuntu screen redraws (just so that I could give myself a chance to get to know the OS a little better).

I've tried editing that xorg.conf thing, but it makes no difference.

**Specs:**

Ubuntu 6.10
ATI Radeon x1950 Pro
Eizo S2411W LCD  (@ 1920 x 1200 native)

---

### Post by tgm4883 on 2007-04-06
Well the drivers are kinda important.  

Also, what have you done to the xorg.conf?  Could you post it?

---

### Post by oomingmak on 2007-04-06
> **tgm4883 said:**
> Well the drivers are kinda important.  
Hello. Thank you for taking the time to respond to my post.  :) 

I have spent in excess of 20 hours trying to install drivers on Ubuntu, and as much as I'd like to have more patience, I'm afraid I just got too p*ssed off to carry on.

I followed 3 different guides (many, many times) and also tried Envy (which just gave an error and wouldn't work either). The problem was every time I tried to install the driver it would break the system so badly that it won't even boot (so there is no way for me to even try to fix it). So then I have to run the Live CD (which for some reason  is way slower on my new build PC than it was on my ancient Pentium2) and then re-install the whole OS and try to install the drivers again.

Seeing as I seem to be getting 1600 x 1200 straight after install, without any add on drivers (although admittedly the performance is rubbish) if I could just get a wide screen equivalent, then at least I could use the OS to lean a few basics in time for the Feisty release in a couple of weeks.

As far as editing the xorg.conf, I follwed a guide that said insert the required resolution as the first item in the first display section in that file (sorry if my terminology is not entirely accurate). I then did ctrl +alt + backspace to re-start the display (is it called "x"?) but it was exactly the same as before. So then I tried re-booting, but still no difference.

I can't post any specific details because I'm back in Windows now (having trashed yet another Ubuntu install).

So I was just curious to know why Gnome provide a GUI display settings manager with various different settings in there, but yet not one single one of them is widescreen :confused:

If screen resolution is meant to be set from the command line, then why provide the GUI tool at all? It all seems a bit half-baked to me.

---

### Post by tgm4883 on 2007-04-06
If you had the correct driver installed then it should work (the gui that is) (I say should as it worked for me before, but not for this computer)

As for the resolution, go into the xorg.conf file and try removing all resolutions on each line of the display (see below for more clarity)

here is my screen section of /etc/X11/xorg.conf
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7300 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
```

What video card do you have? and what version of ubuntu are you running?

---

### Post by oomingmak on 2007-04-06
> **tgm4883 said:**
> If you had the correct driver installed then it should work (the gui that is) (I say should as it worked for me before, but not for this computer)
Ah I see. So the wide screen resolutions would be displayed in the GUI applet once the correct driver is installed?

[QUOTE=tgm4883]
As for the resolution, go into the xorg.conf file and try removing all resolutions on each line of the display (see below for more clarity)[/quote]
Thanks. Orginally I just added the desired resolution as the first value. I'll try removing the other resolutions as you've suggested (that's after I've got round to re-installing the OS yet again - the current install is trashed and completely unbootable).

[http://ubuntuforums.org/showthread.php?t=367820](http://ubuntuforums.org/showthread.php?t=367820)

[QUOTE=tgm4883]
What video card do you have? and what version of ubuntu are you running?[/QUOTE]
Please see the "specs" that quoted in my first post.

---

### Post by tgm4883 on 2007-04-06
> **oomingmak said:**
> Ah I see. So the wide screen resolutions would be displayed in the GUI applet once the correct driver is installed?


Well they should be yea, barring some unforeseen thing.

> **oomingmak said:**
> 
Thanks. Orginally I just added the desired resolution as the first value. I'll try removing the other resolutions as you've suggested (that's after I've got round to re-installing the OS yet again - the current install is trashed and completely unbootable).

[http://ubuntuforums.org/showthread.php?t=367820](http://ubuntuforums.org/showthread.php?t=367820)


I tried just putting it as the first value too and it didn't work.  So I figured that if it was the only value I was going to use and I knew it was right then I would just use that.  Worked ever since

> **oomingmak said:**
> 
Please see the "specs" that quoted in my first post.

Ahh, that would do it.  Since your reinstalling anyway why not just grab a feisty cd and try that.  Seems to be the consensus that edgy is not good.

---

### Post by oomingmak on 2007-04-07
> **tgm4883 said:**
> Since your reinstalling anyway why not just grab a feisty cd and try that.  Seems to be the consensus that edgy is not good.
I was thinking of using Feisty, but when I saw all the comments about really the really slow boot up (among other issues) since Herd 4, I figured that I'd wait for those issues to be ironed out before trying it (especially as the final release is only a couple of weeks away).

Because I am so woefully lacking in understanding of Ubuntu (and Linux in general) I wouldn't necessarily be able to know whether any problems that I experienced were due to beta issues or more whether they were more fundamental problems with Ubuntu itself.

However, seeing as you have said: "*Seems to be the consensus that edgy is not good*" (which is news to me) then I might just download Feisty beta and try it anyway. Got nothing to lose because I'm am getting absolutely nowhere with Edgy (despite pleas for help in other threads where people are having the same problem as me).

Thanks for your time.

---

### Post by tgm4883 on 2007-04-07
I'd download the latest daily build instead of the beta.   If you download the beta, your going to have alot of updates which will bring you up to the daily release anyway.  Not all people have slow boots, mine's pretty quick

---

### Post by oomingmak on 2007-04-08
> **tgm4883 said:**
> I'd download the latest daily build instead of the beta.   If you download the beta, your going to have alot of updates which will bring you up to the daily release anyway.  Not all people have slow boots, mine's pretty quick
Just a quick FYI.

I downloaded Feisty and **finally **I managed to get the ATI drivers installed! 8) 

At last my desktop is running at native resolution (1920 x 1200) and everything is not all stretched horizontally due to my wide screen monitor (well, ........ apart from the Ubuntu splash screen during boot up, but I can live with that).

---

### Post by tgm4883 on 2007-04-08
Ubuntu splash screen will do that.  Last i heard it's hard to get that to detect aspect ratio, and low on the importantance list.

---


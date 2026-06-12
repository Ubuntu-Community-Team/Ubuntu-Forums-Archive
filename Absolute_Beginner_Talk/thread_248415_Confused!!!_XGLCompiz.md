---
title: "Confused!!! XGL/Compiz"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by soutSA on 2006-09-01
Hello,

I have installed XGL/Compiz about 2 weeks ago and everything was working OK and still is awesome. The only problem I have now is that my borders around my windows with the minimize, maximize and close buttons on has gone missing. The only way to get it back now is to switch back to metacity, but that is not the solution.

I have tried to go through the menu of compiz, but it is damn confusing. Has anybody had the same isue and how do I get it back?

Thanks in advance!

:confused: :confused: :confused: :confused:

---

### Post by hanzomon4 on 2006-09-01
Do you have cgwd, If you do you also have the dbus plugin loaded after gconf in your plugin list?

---

### Post by soutSA on 2006-09-01
You got me really confused now. I am still bit new in linux. Where do I go look for the dbus plugin? And how do I know if it is loaded or not?

thanks

---

### Post by Frank Golden on 2006-09-01
> **soutSA said:**
> You got me really confused now. I am still bit new in linux. Where do I go look for the dbus plugin? And how do I know if it is loaded or not?

thanks
I see a lot of stuff posted here by people saying things like "I am new to linux etc" and then they have made a big change by
installing xgl/compiz, which is beta at best software. I am a Ubuntu user
who has been using Ubuntu for a year now. I still have a lot to learn but I consider my self fairly comfortable with Linux.
Of what value is it to install buggy beta software on your
machine if you are new to Linux. I don't mean to imply there is anything wrong with this but why play around with stuff that can seriously screw up your machine for a little "eye candy".

I have tried xgl/compiz several times with limited success.
I have a partimage clone of my pre xgl/compiz Ubuntu so that
I can restore my previous Ubuntu install when something goes inevitably, horribly wrong. I have experienced the problem you described and others that I could not fix. I have come to the
conclusion that xgl/compiz is nowhere ready for "prime time".
The minuses far outweigh the plusses IMHO.

Please don't let my comments and observations dampen your 
enthusiam, it is just that until all the bugs are worked out of
xgl/compiz, my normal Gnome desktop will work fine for me.:)

---

### Post by adam.tropics on 2006-09-01
Which guide did you use to install xgl/compiz? Some of the older guides are really too dated to still be much use...ie the list of what needs to be installed has somewhat evolved fairly rapidly.

---

### Post by tribaal on 2006-09-01
If this helps, I installed XGL/compiz successgully without any hassle using [this guide]("http://ubuntuforums.org/showthread.php?t=245152"). 

I know, it's yet another XGL guide, but it worked for me where others failed.

Maybe Franck Golden has a point, but also don't forget that the best way to learn somthing is by using it, and with trial and error. Just always make sure you have your sensitive data stored safely somewhere (like a DVD backup or something, even external HDDs can fail... but I'm paranoid). 

Like SuSE used to tell you at every loin in the days:
"Have a lot of fun" :)

- trib'

---

### Post by hanzomon4 on 2006-09-01
Ok I'll try to walk you through the dbus/cgwd thing.

1. Press alt and F2, A little box will pop up. In that box type gconf-editor

2. With gconf-editor now open click on the following folders apps>compiz>general>allscreens>options. 

3.There will be a window besides the row of folders. The first option in this window should be "active_plugins. This is a list of all compiz plugins you have loaded.

4. Double click the option "active_plugins". A new window will pop up with the title "Edit Key". 

5. In this window click the "Add" button. A little box will pop up, type dbus and click "OK".

6. Now click the "UP" button intill you see "dbus" right under "gconf". Now just click "OK"

That does it for dbus, Now for cgwd.

I think you have already done the rest of this stuff, but I'll post it just to be through. 

1.Click on the "Applications" menu on the bar at the top of your screen. Go to Accessories and click on Terminal.  

2.Cut and paste the following command in to the terminal ```
sudo apt-get install compiz compiz-plugins compiz-core cgwd cgwd-themes
```

If step 2 doesn't work it only means you need to add the compiz-quinn repo(You have most likely done this already)

Last start compiz like so.

1. Open a terminal and cut and paste the following.
```
 sudo gedit /usr/bin/thefuture
```

2. A text editor window will pop up. Cut and paste this into the the editor.
```
#!/bin/bash 
cgwd  --replace &
 
compiz --replace gconf
```
Save it, then close the editor window.

3.Cut and paste this in the terminal window.
```
sudo chmod 755 /usr/bin/thefuture
```

4.With all that done cut and paste this in the terminal window.
```
thefuture
```

And for up-to-date info on compiz checkout the [Compiz forums]("http://www.compiz.net/")

---

### Post by TFX360 on 2006-09-01
Did someone say eyecandy?


[IMG]http://home.casema.nl/d.sluijter/eyecandy.png[/IMG]

I've been using linux for about two to three months now. Compiz/XGL is in my opinion not buggy. And you got to love the eyecandy. This is also making Ubuntu a lot more populair! I'm not saying you should install it. Especially when you do not know what **B**ourne-**A**gian **SH**ell is.


Swoong!

---

### Post by hanzomon4 on 2006-09-01
Nice! I agree xgl/compiz is not really buggy once you have it setup.
Although There was this one time awhile back when upstream changes to compiz caused some major issues with compiz-quinn, but all is well now

---

### Post by TFX360 on 2006-09-01
> **hanzomon4 said:**
> Nice! I agree xgl/compiz is not really buggy once you have it setup.
Although There was this one time awhile back when upstream changes to compiz caused some major issues with compiz-quinn, but all is well now

It is kinda beta-ish with an update a day keeps the bed bugs away.

---

### Post by Frank Golden on 2006-09-01
> **TFX360 said:**
> It is kinda beta-ish with an update a day keeps the bed bugs away.
I can live without it.

---

### Post by Frank Golden on 2006-09-01
> **TFX360 said:**
> It is kinda beta-ish with an update a day keeps the bed bugs away.
I can live without it. I will give tribbal's link a try though.

---

### Post by TFX360 on 2006-09-01
> **Frank Golden said:**
> I can live without it. I will give tribbal's link a try though.

On my laptop I can, on my desktop I can't. It rocks, especially the XglGoodies.


:D

---


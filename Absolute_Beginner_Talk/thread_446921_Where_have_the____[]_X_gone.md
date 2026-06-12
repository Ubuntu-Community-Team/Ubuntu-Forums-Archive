---
title: "Where have the  _ [] X gone"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Kouki on 2007-05-17
Since installing Feisty and Beryl my windows no longer have the minimise, maximise and close symbols in the top right hand corner.  It's really annoying having to file close everything.

Could someone tell me where they've gone and how I can get them back please.

Thanks!

---

### Post by starcraft.man on 2007-05-17
> **Kouki said:**
> Since installing Feisty and Beryl my windows no longer have the minimise, maximise and close symbols in the top right hand corner.  It's really annoying having to file close everything.

Could someone tell me where they've gone and how I can get them back please.

Thanks!

Sounds like you've run into a minor glitch with Beryl, just a quick idea to try and fix is to reload the window manager/decorator... Right click on your Beryl Gem in the tray, then select "Reload Window Decorator/Manager" Try each of them separately, that might fix it. 

Otherwise, something must have gone wrong with the way you installed beryl and I'd tell you to reinstall it. By that you would be best served by switching to Gnome/metacity and then removing beryl however you put it in. This is a good guide to follow to [install]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy") (pick ATI or nvidia depending your card).

---

### Post by netwerx on 2007-05-17
which theme in beryl are you using?  there are a couple themes that dont have the buttons

---

### Post by starcraft.man on 2007-05-17
> **netwerx said:**
> which theme in beryl are you using?  there are a couple themes that dont have the buttons

Well, he didn't say he changed the default emerald theme... if you want to make sure its not the theme, right click on the beryl gem and select emerald theme manager. Then just select any theme other than the one your on now. If you get that error on more than 3 its definitely not a theme issue...

---

### Post by netwerx on 2007-05-17
> **starcraft.man said:**
> Well, he didn't say he changed the default emerald theme... if you want to make sure its not the theme, right click on the beryl gem and select emerald theme manager. Then just select any theme other than the one your on now. If you get that error on more than 3 its definitely not a theme issue...

he also didn't say he didn't, my good man.
:P

---

### Post by lazyart on 2007-05-17
Quit Beryl from the gem icon, then use Alt-F2 to bring up a terminal window and type metacity.  This will bring back the default window decorator.

In the end you have to decide to reinstall or uninstall Beryl.

---

### Post by compmodder26 on 2007-05-17
This is a common problem with Nvidia cards.  If you have an nvidia card, try adding this line:

```
Option         "AddARGBGLXVisuals" "True"
```

under the "Device" section in your xorg.conf file (/etc/X11/xorg.conf).

Restart the x server (Ctrl+Alt+Backspace).

After logging in, your borders should be in place.

---

### Post by Kouki on 2007-05-17
Thanks for the tips, it seems that the default emerald theme may have malfunctioned (here is a screenshot)

[IMG]http://i16.photobucket.com/albums/b15/stuarthyden/Screenshot-2.png[/IMG]

I also don't seem to have an apply button or the equivalent so I can't change it to another theme?  I can set it back to metacity and they come back, but obviously this isn't why I installed beryl.

Before I reinstall it, can I just check with you that I'm not doing something stupid and missing how to change the themes without an apply button?  (Double clicking the theme I like doesn't work).

---

### Post by lazyart on 2007-05-17
Nope, no apply button... I've seen this a lot in linux apps and it takes some getting used to.  Selecting it does just that-- it's selects it!

---

### Post by netwerx on 2007-05-17
Click on the theme you want, it should auto-change.
then hit ALT + Q to quit the window

just checked it for ya!

good luck

---

### Post by Kouki on 2007-05-17
> **lazyart said:**
> Nope, no apply button... I've seen this a lot in linux apps and it takes some getting used to.  Selecting it does just that-- it's selects it!

Sadly not on mine :frown:  I select it, quit and still nothing.

Looks like I'll have to reinstall it.  Trust it to mess up for me, I installed it by the book using the ubuntuguide.  Ah well.

It doesn't auto change I'm afraid.  I click on my desired theme, it becomes shaded as the first one is on the screen shot and that's it.

---

### Post by Kouki on 2007-05-17
Thanks for the tips, I've fixed it now.

I tried reinstalling all the Beryl bits using Synaptic.  This didn't work and it remained the same.

Then found this guide and followed the 123 steps, it works at last!

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia)

Thanks and thanks to whoever wrote that page :guitar:

---


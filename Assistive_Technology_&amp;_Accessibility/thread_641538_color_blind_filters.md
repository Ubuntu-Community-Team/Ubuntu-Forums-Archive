---
title: "color blind filters"
date: 2007-12-15
forum: Assistive Technology &amp; Accessibility
---

### Post by gwm on 2007-12-15
Hi,
I read on wikipedia about gnome-mag and an applet that lets one switch colors. I found the software using synaptic and installed it but where is it? How do I use it?  I don't find any instructions.
Please can somebody help?

---

### Post by joann on 2007-12-22
Hello gwm,

To answer your question about gnome-mag. Gnome-mag is a magnification tool that can provide screen magnification and inverse the color on you screen. Gnome-mag can be accessed on the command line through the program "magnifier" that is located in the /usr/bin folder. To get a better idea of what this program is capable of type "magnifier --help" to get a full list of its usage or just "man magnifier". It sound to me like you might want to try running the program with "magnifier -i -z 1". This will start the program at a magnification level of 1 (no magnification) and inverse the colors on the screen.

You may also want to look into the enabling desktop effects as another option. The composite extension allows for more than just neat graphics effects. It also allows for other more exciting features for accessibility such "desktop-zoom" and "color filters". I think you may find the "color-filters" useful, because with this feature enabled you can place a color filter on the screen. There is an array of choices from negative, bluish-filter, sepia, and greyscale. With composite enabled, I was able to use a few shortcut keys to toggle between the different filters. In order to enable this functionality on my system I went to System->Preferences->Appearance. I then when to the last tab on the right in the appearance window and enabled Desktop Effects. The I proceeded to click Custom Effects. This closed out of the previous window and opened a new window that allowed me to customize accessible feature including "color-filters" and "desktop-zoom". This same window that opened up and allowed me to customize the accessibility features for compiz can be found under System->Preferences->Advanced Desktop Effects Settings. I believe the name of this customization tool was Compiz Configure. The idea behind composite is actually really neat. Before a window is drawn to the screen it is stored memory and then the composite manager uses this memory to draw to the screen. It is a very effective use of the hardware and allows for things like transparencies to occur very quickly. 

I hope this is helpful. If you have any questions feel free to post back.
Happy Holidays,
Joannah

---

### Post by gwm on 2007-12-22
Thanks Joannah,
I've seen references to Compiz Fusion while exploring this thing, but nothing straight forward that tells me how to get it going. I tried to follow your instructions but bumped my head both tiimes.

Magnifier complains about source and target screens as follows:
(magnifier:12175): Bonobo-WARNING **: Assigning a default value to a non readable property 'source-display-screen'

(magnifier:12175): Bonobo-WARNING **: Assigning a default value to a non readable property 'target-display-screen'

The screen flashed, but I couldn't see any difference, so I guess it didn't work.

When I went into System->Preferences->Appearance, my tab on the right is [BVisual Effects][/B] not Desktop Effects. The choices presented to me are **None,** **Normal** and **Extra.** I tried each in turn. No **Custom Effects** is ever offered to me. I therefore assume that you have something installed that I haven't. Synaptic indicates to me that I have Conmpiz installed - all except something called gnome-compiz-manager, but gnome-compiz seems to be a manager instead.

I hope you can help further. In the mean time you have told me where compiz fusion is hiding and you have opened up some new leads for me.

Thanx again,

:popcorn:

---

### Post by Sef on 2007-12-22
> When I went into System->Preferences->Appearance, my tab on the right is [BVisual Effects][/b] not Desktop Effects. The choices presented to me are None, Normal and Extra. I tried each in turn. No Custom Effects is ever offered to me. I therefore assume that you have something installed that I haven't. Synaptic indicates to me that I have Conmpiz installed - all except something called gnome-compiz-manager, but gnome-compiz seems to be a manager instead.

Go into Applications > Add/Remove > search and type in "CCSM" (without the quotes.)  That will give you the Advanced Desktop Settings Manager, which controls the settings for Compiz-Fusion.

---

### Post by joann on 2007-12-22
gwm,

You where in the right place with visual effects. Since it might not hurt to try a few keyboard combinations to see if they work, try going to visual effects and checking extra to enable the composite features. Once the effect are enabled try pressing the <Super>D to turn on compiz's filters and then <Super>S to cycle through the available filters. In order to get this to work I had to press Super+D quite a few times before I pressed Super+S to toggle. (The super key is the windows key.) If this does not work you might want to try to use synaptic package manager or apt-get to install a few more compiz related software packages. With these installed and working you should be able to get the color filters going via compiz.

I forgot, and I forgot to tell you that when I installed my system I also went through and installed a few of the compiz goodies that where offered on the synaptic package manager. This might be what you are missing. The software that Sef suggested is one you need, but I could not find it on my system by going to add/remove under the applications menu. (This might just be me). I did a search with synaptic package manager looking for compiz and installed the following components on my machine in order to enable the composite manager and all of the neat effects. So, here is the list of software I installed. I hope this helps to clarify exactly what you might need:

compiz
compizconfig-setting-man
compiz-core
compiz-dev
compiz-fusion-plugins (both extra and main)
compiz-gnome
compiz-plugins
gnome-compiz-mananger
libcompizconfig
libgnome-compiz-manager

Good luck,
Joannah

---

### Post by cerdiogenes on 2007-12-24
gnome-mag have an applet that permits to apply filters to colorblind users, but this isn't shipped with Ubuntu. If you want to try it you must install the libcolorblind0-dev package and compile gnome-mag by hand.

---

### Post by gwm on 2007-12-25
Thanx all,
I have now found that **CCSM** stands for **Compiz Configuration Settings Manager**. When I installed it, most of the other things in Joannah's list came too. The menus she referred to all appeared as described.

Next I enabled the color filter and clicked on the option and it presented me with some options. Thus far, if I've highlighted some text, the highlight changes color fleetingly whenever I press any one of super-S, super-D or super-F. No toggling or cycling through filters occurs and nothing else on the screen changes in any way that I can see.

Perhaps I need to reboot or something.

I'll go google this thing and see if I can find out what is supposed to happen. Perhaps there is some help or documentation somewhere.

Thank you all once again,
:popcorn:

---


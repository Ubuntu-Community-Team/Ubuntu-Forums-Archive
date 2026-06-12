---
title: "Had enough! Ati and Compizfusion"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Sugz on 2007-12-09
I have had it to here *raises hand above head* with This nonsense with the simple task of
Installing, updating, Ati drivers and finally using Compiz Fusion. 

So here is the current situation. 
I want to uninstall All remenants of Any Ati-drivers that i haev cluttered around and start with a fresh install of the latest Ati Drivers (Which i believe done require you to install GLX)
And finally install Compiz fusion. 

Why on earth is this such a headache of a task. It was a doddle on my laptop but this is in an entirely different league. 

So please anyone. how do i install the new Ati drivers and Compiz fusion in a safe mano>
Many thanks

-Sugz

---

### Post by Lvcoyote on 2007-12-09
Which version of Ubuntu??

---

### Post by Sugz on 2007-12-09
ha i just this second remembered that i left it out. sorry.
its 7.04 Feisty
Thanks

---

### Post by Lvcoyote on 2007-12-09
howtoforge.com has a 7.10 tutorial, it might be close enough to work with 7.04

---

### Post by Teknyk on 2007-12-09
This one worked for me but it is for Gutsy.
[http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+gutsy+compiz](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+gutsy+compiz)

I had it easy though. Mine was a fresh install not an upgrade.

---

### Post by CaptainInsaneO on 2007-12-09
It's such a headache because ATI doesn't like to make drivers for Linux. :(

---

### Post by Natr0n on 2007-12-09
> **Teknyk said:**
> This one worked for me but it is for Gutsy.
[http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+gutsy+compiz](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+gutsy+compiz)

I had it easy though. Mine was a fresh install not an upgrade.

If you feel like installing 7.10, following the instructions in that link will most likely work.

---

### Post by Sugz on 2007-12-10
Hmm well im using Wubi 7.04 as im not at all comfortable with partitioning my HD at all. 
But thanks for that input, ill see if it helps. 
be back in touch
-Sugz

---

### Post by kelvin spratt on 2007-12-10
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) This is a link to Envy you can then uninstall your existing drivers drivers with the program and it will then install the latest ATI drivers for your graphics card. ATI are now trying to support more cards for Linux and the drivers work for me.

---

### Post by Supreme1012 on 2007-12-10
yea, envy worked well for me. before that trying to get the driver to work was a losing struggle for me. envy makes it easy

---

### Post by bobbob1016 on 2007-12-10
Unless you have a x1*** or greater, you don't NEED the ATI drivers.  They might help, but they aren't NEEDED, from what I hear.  Might get better performance with them, but it'll work without.  I don't have them on this computer, with an x600.

---

### Post by Sugz on 2007-12-10
Ok so if as a fallback, is there a way to revert back to the defailt "Ati" drivers that came with Ubuntu Feisty?

---

### Post by meindian523 on 2007-12-10
System>>Administration>>Restricted Drivers Manager

Uncheck the Enabled box and:

[http://ubuntuforums.org/showthread.php?t=536149](http://ubuntuforums.org/showthread.php?t=536149)

maybe this helps.....

---

### Post by Sugz on 2007-12-10
UPDATE######

I managed to install the new Drivers Finally!
But
Beryl works flawlesly But Compiz Fusion Refuses to run. with the output as follows.

andy@hh206a:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

But how on earth did Beryl work so well?
I converted to Compiz fusion because the Window Borders would not show up in Beryl.

---

### Post by meindian523 on 2007-12-11
According to the error,you need Xgl to run compiz...Do
```

sudo apt-get install xserver-xgl
```

---

### Post by dgrafix on 2007-12-11
NOOOO!

It sounds to me like you simply need to whitelist the card. I had that same problem and found a solution somewhere. Take the XGL road and you will end up with a horribly slow graphics system with no direct acceleration for games or other 3D stuff. (try "glxgears" command and "glxinfo | grep direct" both with and without xserver-xgl if you dont believe me!)

What i did was use ENVY to install the latest driver (which is the only one that supports composite without XGL) then whitelist the driver. Its something like "sudo gedit /etc/compiz" or something, type "locate /etc/compiz" to find what it should be called. And look for the whitelist section and add "fglrx" (check that spelling) to the list.

reboot and it should work.

If you end up as one of the unlucky that needs XGL just to run compiz then you are better off without it. Wobbly windows just isnt worth the slowdown. However if you have a half decent ati card it should work.

---

### Post by zeller on 2007-12-11
You could try what I did and see if it works for you...

Read [this](http://ubuntuforums.org/showthread.php?t=586038) thread.

Also, I had to change my driver in my xorg.conf file to "radeon" instead of what was there.

Everything has worked fine since. I have an x600 ATI too.

*shrug* ...try everything.

---


---
title: "Screen resolution problems..."
date: 2008-04-02
forum: Apple PPC Users
---

### Post by PaintballMan10988 on 2008-04-02
Hello all,

I am running 7.04 Feisty Fawn on my iBook PPC G3 laptop.  I have Ubuntu installed and everything is running alright, with the exception of my screen.  For some reason, my desktop does not fill the screen.  There is a black bar of death on the right hand side of my screen, and my desktop repeats itself at the bottom of my screen.  I have tried changing the screen resolution under the Preferences with no effect, other than the desktop getting smaller.

I think the problem is something to do with my graphics card, but I am an Ubuntu novice, and don't know what to do next.

Any help?  Let me know if I need to provide more info.

Thanks!

Mike

---

### Post by slacka-vt on 2008-04-02
try this in your terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

~s

---

### Post by stream303 on 2008-04-02
You may still have to manually edit your /etc/X11/xorg.conf file.  Make a backup first.

Sounds like the system is picking up a 1024x768 resolution when you need 800x600.  You can check the model and specs here for the G3 ibook:

[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

You can also try this but [B]use extreme caution as incorrect resolutions and frequencies can damage your monitor - so only do this if you are SURE of your specs.
[/B]
```
xrandr -q
```

You will see a list of known resolutions, but not all of them work.

If your system is 800x600 for example, you could try:

```
xrandr -s 800x600 -r 60
```

and then go back into the screen resolution prefs to see if you can pick it up.

Be sure to keep these two faqs handy:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

If none of this works, I'm sure you could manually edit your xorg.conf file..

---

### Post by PaintballMan10988 on 2008-04-02
I pulled up the resolution list using the xrandr command, but the highest resolution given is 800x600.  My monitor's native resolution, according to the Apple specs, is 1024x768.  It does not give a default refresh rate, but I'll assume it is 60 hz.  How _exactly_ do I edit the xorg.conf file?

Thanks for the help.

Mike

---

### Post by PaintballMan10988 on 2008-04-02
I messed around with the settings and conf file and managed to get it to restart with the right settings.  It all works now, you guys are awesome and saved my computer.  No more death bar.

Thanks a ton

Mike

---


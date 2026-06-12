---
title: "Window/Scroll Lagging"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Heous on 2006-11-12
Hello everyone.

Recently, I changed my screen resolution from 1024x768 to 1280x1024 and my refresh rate from 60 hZ to 85 hZ (both of which my monitor supports).  However, I have a problem:  Whenever I move windows around or scroll in programs, it lags really badly.  The windows will leave a visible trail behind them as they're moving, and Firefox will "skip" (in order words, it won't scroll up and down fluently, like it should).  My graphics card is an ATI Radeon X800 SE.  I tried installing the appropriate Linux drivers for this card from ATI's website, but I get the following answer whenever I try to execute it:

Could not open the file /home/heous/Desktop/ati-driver-installer-8.30.run

```
gedit has not been able to detect the character coding.  Please check that you are not trying to open a binary file.  select a character coding from the menu and try again.
```

I try both types of character coding offered, which are:

```
current locale (UTF-8)

or 

Western (ISO-8859-15)
```

Please help with this, I'm pretty much a complete Linux newb and have been using Windows for the majority of my lifetime.  This screen lag thing is a real pain, and I'd like to fix it ASAP.

Thanks in advance,
Heous

---

### Post by jordanmthomas on 2006-11-12
You shouldn't try to open the file in gedit.
Right click on it and go to properties.
Go to the Permissions tab and allow the owner to execute
Close the window
Now, double click on it and choose to run in a terminal.

See if you can get any further with that.  :)

---

### Post by Heous on 2006-11-12
Ok, I got the drivers installed, but the lag problem seems to persist.

---

### Post by jordanmthomas on 2006-11-12
Have you set up your xserver to use the new drivers and restarted X yet?

If not, maybe you should look around on the forums for how to properly install the drivers.  If you have already done all this, then I don't know what the problem is and someone with an ATI card might need to help.

---

### Post by Heous on 2006-11-12
xserver?  x?  You've lost me.  :(

---

### Post by jordanmthomas on 2006-11-12
Have you edited the file
```
/etc/X11/xorg.conf
```?

If not, then you're not done installing the drivers.
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

should be of some help to you.  Personally, I have been graced with a graphics card that has open source drivers that work well so I haven't had to do much in the way of installing drivers.  It shouldn't be too bad though.

Good luck

---

### Post by Heous on 2006-11-12
Success!  Apparently, all I had to do was configure the xorg file to use ATI drivers instead of vesa, whatever those were.  Thanks for the help! :)

---

### Post by jordanmthomas on 2006-11-12
Glad to hear it works.

---


---
title: "change screen resolution"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-04-23
hi,
   It won't let me change my screen resolution from 640x480. Is there anything i can do?

---

### Post by freebird54 on 2007-04-23
Relax - there are many things you can do.  To be very specific, we will need more information though!  What version have you put on, what video card are you running etc.  We could just give a generic answer, but it is better if we know a bit more :)

---

### Post by Dark-Angel on 2007-04-23
got 6.06 and the video card not too sure.

---

### Post by freebird54 on 2007-04-23
Ok - we'll do what we can then.  Open up a terminal window (found in Applications->Accessories->Terminal)  Copy the following code and paste it into the window:

```
sudo dpkg-reconfigure xserver-xorg
```

When you press <enter>, it will go through a lot of questions as it sets up your xServer.  Here is a link you might want to have open when you do it!

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

as it explains what to do.  Mostly - just accept the defaults.  When it asks for a video driver, vesa is a safe choice - but not the best for peformance!  When it comes to your resolution settings, put a mark beside all the ones you want (and KNOW your monitor can do), and clear the others.  <space> toggles the marks.

Once you can see what you're doing :) we can find out what you're running and upgrade it later, OK?

Good luck

---

### Post by Dark-Angel on 2007-04-23
ok i did that. i go to screen resolution and click on the arrows to change it but does nothing. Not sure

---

### Post by freebird54 on 2007-04-23
The choices you made should now be available in System->Prefernces->Screen Resolution.  To check what you have set now, can you paste the output from the following terminal command?

```
cat /etc/X11/xorg.conf
```

It would help me to know what is set, and I could point out changes you might want to make.

---

### Post by thefoolisme on 2007-04-23
I'll be watching this thread because I encountered the same problem yesterday.  Resolution would only show at 640x480, and I went through the xorg to ensure that several were checked and supposedly available.  

My video card is a simple integrated laptop one.

---

### Post by freebird54 on 2007-04-23
Same recommendation - do the dpkg-reconfigure thing.  Another route to success can be in xorg.conf by ensuring that  HorizSync and VertRefresh values are in your monitor defintiion.  Like so:

```
Section "Monitor"
        Identifier   "Samsung_900iFT"
[B]        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
[/B]        Option      "DPMS"
EndSection
```

Obviously these number won't work for you - but if they are not there it could mean that your screen's capabilities were not detected, and out of fright/excess of care it set things to a known 'anyone can run this' setting.  Find the specs of your laptop screen, and fill in sensible values for Sync and Refresh and it should allow greater resolutions.  If you're in dpkg the monitor section does this automatically (more or less) when you choose your 'best resolution' setting...

Hope this helps!

---


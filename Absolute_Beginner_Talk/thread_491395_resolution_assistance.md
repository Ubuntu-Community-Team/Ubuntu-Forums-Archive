---
title: "resolution assistance"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-07-03
im using a nVidia GeForce2 MX/MX 400
it used to run under windows at 1600x1200 just fine
but now in ubuntu it wont go any higher than 1280x1024
can anyone help?

---

### Post by edwardLS on 2007-07-03
I have had a similar problem, but not with the video card you mentioned.  
I would check in the /etc/X11/xorg.conf file to see what video resolutions are available. If the resolution you are capable of, and desire, is not in that file, you may need to edit the file and add the appropriate resolution settings.

---

### Post by Rocket2DMn on 2007-07-03
Be sure to make a backup of the xorg.conf file first
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
You can edit the file and restart X using CTRL+ALT+BACKSPACE.  If X fails to reload, you will have a terminal - restore your back up by:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

If your editing fails despite seeming correct, you can run
```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through a process of setting up hardware, most importantly your video stuff.  Please don't ENTER your way through, do read it.  When you get to the resolutions screen you can hit TAB to move through the options and SPACEBAR to select.  You should choose your monitor's max resolution and everything less than that.

---

### Post by Raineer on 2007-07-03
If you choose to manually edit xorg then make your changes here:
> Section "Screen"
  Identifier "Default Screen"
  Device "nVidia Corporation G71 [GeForce 7900 GS]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1600 1200
    modes [COLOR="Red"]"1024x768@60" "1152x864@75" "1024x768@70" "1280x1024@75"[/COLOR] 
    depth 16
    virtual 1600 1200
    modes [COLOR="Red"]"1024x768@60" "1152x864@75" "1024x768@70" "1280x1024@75"[/COLOR]
    depth 8    
    virtual 1600 1200
    modes [COLOR="Red"]"1024x768@60" "1152x864@75" "1024x768@70" "1280x1024@75"[/COLOR]
  EndSubSection
EndSection 
The dpkg... option works fine too and should make a backup for you of xorg.2007070307(bunch of numbers that mean date and time)

---


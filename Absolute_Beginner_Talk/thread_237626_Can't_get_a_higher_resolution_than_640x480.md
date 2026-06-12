---
title: "Can't get a higher resolution than 640x480"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by mywhitenoise on 2006-08-16
why is that?  In fact, it's the only option I have for the resolution.

I'm completely new to Linux, and just installed it on my girlfriends laptop, but so far it's a bit of a hassel, as it's only taking up half the screen.

---

### Post by zeh on 2006-08-16
Hi.

Tell us the specs of your girlfriend notebook, including the video card. What version of ubuntu are you using?

---

### Post by mywhitenoise on 2006-08-16
I'm not exactly sure the full specs of her graphics card, or laptop, i'm a mac user so this is all kind of foreign to me.  The notebook is a Dell Inspirion 1100, 30 GB drive, Intel Pentium 4 2.2 GHz.
Display adapters - Intel 82845G/GL/GE/PE
GV Graohics Controller

and we installed the Ubuntu 6.06.1 LTS release.
Thank you for any help, and the quick response.

---

### Post by rck_hitokiri on 2006-08-16
tr this out......

code:
sudo dpkg-reconfigure xserver-xorg

(when the blue screen pops open you can select yes up until you get to the monitor detection option. then deselect 640x480. Leave 800x600 and 1024x768 then select 1280x800 or any of your choice. crt+alt+backspace to go back to login.

 if this dont work out try posting back for more info.


cheers.

---

### Post by Cartwheels4amile on 2006-08-16
Well would you look at that. I'm having the same exact issue, except my computer is a Toshiba Tecra 530cdt

Here's a (hopefully) working link to a PDF of the system's specs. [http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_outFrm.jsp?moid=1073769647&ct=DS&soid=637982&BV_SessionID=@@@@1621365237.1155755539@@@@&BV_EngineID=cccdaddiifjhfihcgfkceghdgngdgnn.0](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_outFrm.jsp?moid=1073769647&ct=DS&soid=637982&BV_SessionID=@@@@1621365237.1155755539@@@@&BV_EngineID=cccdaddiifjhfihcgfkceghdgngdgnn.0)

---

### Post by arjun.shankar on 2006-08-17
I would try installing '915resolution'. I had this problem with a friend's 915 motherboard once, and it worked for me (it also works for 845G, 855G and 865G chipsets ;)). The package can be downloaded thro apt-get:

**sudo apt-get install 915resolution**

Read up how to use it with this:
**man 915resolution**

---

### Post by zeh on 2006-08-18
Hi mywhitenoise,

If none of these suggestions work, post your xorg.conf file here. It´s in /etc/X11. I think forcing xorg to your notebook native resolution will work.

Try this:

backup your original xorg.conf
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp 
```

now open the xorg.conf file.
```
 sudo gedit /etc/X11/xorg.conf 
```

There´ll be something like this on the file:
```

Section "Screen"
Identifier "screen1"
Device "device1"
Monitor "monitor1"
DefaultColorDepth 16

Subsection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubsection

Subsection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubsection

Subsection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubsection

Subsection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubsection
EndSection

```

Set DefaultColorDepth to 16 and remove the 800x600 and 640x480 options from the 16 and 24 depth.
```

Subsection "Display"
Depth 16
Modes "1024x768"
EndSubsection

Subsection "Display"
Depth 24
Modes "1024x768"
EndSubsection
EndSection

```

If your x server crashes, log on console and restore your old xorg file.

```
 sudo cp /etc/X11/xorg.conf.bkp /etc/X11/xorg.conf 
```

Hope this works...

---

### Post by HeresJohnny on 2006-10-04
Thanks, Zeh.  I was able to fix a similar problem thanks to your instructions.  Hooray Zeh!!!:D

---


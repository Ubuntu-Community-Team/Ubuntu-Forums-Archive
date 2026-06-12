---
title: "Ubuntu won't load... think I messed graphics up"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by brockstrap on 2008-03-13
Hi, I'm a complete novice at this. I d/loaded ubuntu couple of days ago and installed it as a dual boot with Vista on a Toshiba Equium laptop. After spending many hours loving trying to get various things on it working (e.g. wireless) I get it up and running alrigt.

Today I tried to get the desktop effects working... which I did for a short while, then I restarted after messing round with Envy (dont really know what I was doing - uninstalling Nvidia or something) and it all went pear shaped!

When I load up now it goes to the login screen then password screen, then black... then back to the login screen again...

When I type 'compiz' into the safe-mode terminal I get this...

Checking for Xgl: xvinfo: unable to open display
not present
xset: unabe to open display ""
AIEEEEH, no log file found
xset: unable to open display ""

Blacklisted PCIID '8086:2902' found
aborting and using fallback: /usr/bun/metacity
Window manager error: Unable to open X display  

(I hope thats accurate.. I had to write it out by hand :-( )

Any help with this would be greatly appreciated,
Ta, Adam

---

### Post by Rocket2DMn on 2008-03-13
OK, let's start by uninstalling the envy stuff, then getting your drivers back to the way they were before.  Do CTRL+ALT+F1 to get to a tty (a full screen terminal, essentially), login there, and run
```
sudo envy --uninstall-all
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then you can restart gnome
```
sudo /etc/init.d/gdm restart
```

---

### Post by brockstrap on 2008-03-13
Cheers mate...

Ill scribble that down and have a go!

---

### Post by brockstrap on 2008-03-13
OK, I tried those. Went through a setup as well.
But still the exact same thing happening, and compiz says the same (dont know if that help..?)... Really dont know what to do.

---

### Post by Rocket2DMn on 2008-03-13
OK, but are you back to where you were before with decent screen resolution outside of safe mode graphics?
Have you tried the restricted drivers for your nvidia card from System->Administration->Restricted Drivers Manager?

---

### Post by brockstrap on 2008-03-13
Erm.. no.

When I load up in safe-mode.. I just get a command prompt. 

At the moment when loading the normal way, its still giving me the login and password screens... then black... then back to the login screen..

Sorry not very clear

...the screen resolution looks normal when its asking me for username and password...

---

### Post by Rocket2DMn on 2008-03-13
OK then, you're going to need to try to reconfigure X manually, here's how: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
The point is to get back into the GUI.

It told you
> Blacklisted PCIID '8086:2902' found
That means that your video card is not supported for Compiz Fusion.  Can you please post the output of
```
lspci | grep VGA
``` when you are back in the regular GUI?

---

### Post by brockstrap on 2008-03-13
Ok cheers, Il have a look at that.

lspci | grep VGA say:

00:02: VGA compatible controller : Intel corporation Mobile GH965/GL960 integrated graphics controller (rev 03)

---

### Post by brockstrap on 2008-03-13
I tried your suggested forum link..but alas the same problem.. Grr, so annoying. Thanks very much for your help.. i think il give it more time 2mor. Any more suggestions?

---

### Post by Rocket2DMn on 2008-03-13
Did you select the "intel" driver?  Please post your xorg.conf for me:
```
cat /etc/X11/xorg.conf
```

---


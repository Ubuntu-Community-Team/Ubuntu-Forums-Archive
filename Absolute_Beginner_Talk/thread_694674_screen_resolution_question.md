---
title: "screen resolution question"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by sinjin67 on 2008-02-12
Greetings all,

I am about as new as you get. My question is about settings
screen resolution.. When I am working with the live cd I can 
reset the resolution to 1024x768 and the picture looks great.

I then install to the hard drive using the guided prompts,
everything seems to go fine during install process but upon
reboot the screen is well "un-readable"  the resolution is completly
off. 

So why does the live CD work and the installing to the 
hard drive fail ? 

If I leave the default resolution which is 1280x???, it will install
to my hard drive ok and I can see the screen but with vertical
lines like the its overamping the hertz.

Any help would be great..

Peace

---

### Post by taurus on 2008-02-12
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, get back to GUI login screen with <Alt>F7 and restart X again, <Ctrl><Alt>Backspace.

---

### Post by Ferri on 2008-02-12
Could you tell us what graphic card do you have?
You may try, from command line:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
The password is the same as your user.

---

### Post by sinjin67 on 2008-02-12
I believe its an Intel Video Card, not sure on model - built into MB. But I will find out here shortly and get back.

Thank you for the tips already provided..

---

### Post by Jimcanoa on 2008-02-12
Type lspci in the command line and paste us the output... no need to look for the manual ;)

---


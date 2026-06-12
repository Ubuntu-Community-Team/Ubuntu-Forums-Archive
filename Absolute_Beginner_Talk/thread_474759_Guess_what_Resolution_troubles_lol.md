---
title: "Guess what? Resolution troubles lol"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Yours Truly on 2007-06-15
Yep same here i have all the resolutions to choose from but if i choose anything else except 1024x768 it will mess up. I normally run at 1920x1200 so thats my ideal resolution im looking for :)

I have seen threads where people say edit the xorg.conf i tried that and cant as its read only i also tried the sudo thing in the terminal but when it prompts me for a pass it doesnt let me enter one.

Suggestions? :)

---

### Post by nitro_n2o on 2007-06-15
First of all it does let you enter the passwd.. but you won't see anything typed "no windows asterisks **" 
wht is your video card?

---

### Post by Yours Truly on 2007-06-15
Well i type and nothing like appears i tried typing it it just sys bad password and Mobilit Radeon x700 =]

---

### Post by nitro_n2o on 2007-06-15
I don't really understand wht is going on.. but if you want to edit xorg.conf 
use 
for console editing:
```
sudo vim xorg.conf
``` 
for gui: 
```
gksudo gedit xorg.conf
```
Then console will say 
```
password:
```
After than type in the password you'll not see anything in the screen, but it's there.. 
so type in the password and hit enter

---

### Post by timcredible on 2007-06-15
have you installed the ati driver?  that's the only way to go above 1024x768 with an ati card.  it's available in synaptic.  i could only run 800x600 on an ati x1500 until i installed drivers, then, after a reboot, it automatically detected everything and was running 1920x1200.

---

### Post by Yours Truly on 2007-06-15
It lets me choose it but this it what happens when i use it =[

[IMG]http://www.uploadz.co.uk/356screenshot.png[/IMG]

---

### Post by nitro_n2o on 2007-06-15
did u try  to restart x (CTRL+ALT+backspace)

or maybe you wanna try
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Yours Truly on 2007-06-15
> **timcredible said:**
> have you installed the ati driver?  that's the only way to go above 1024x768 with an ati card.  it's available in synaptic.  i could only run 800x600 on an ati x1500 until i installed drivers, then, after a reboot, it automatically detected everything and was running 1920x1200.
I tried downloading the drivers and it couldnt read the file?

---

### Post by Yours Truly on 2007-06-15
Im having problems running the .run file

---

### Post by timcredible on 2007-06-15
> **Yours Truly said:**
> I tried downloading the drivers and it couldnt read the file?

it's in synaptic - xserver-xorg-video-ati.  always try to use synaptic instead of installing by hand.

---

### Post by Yours Truly on 2007-06-15
> **timcredible said:**
> it's in synaptic - xserver-xorg-video-ati.  always try to use synaptic instead of installing by hand.
Sorry dude i only got this installed today :)

How would i go about this?

---


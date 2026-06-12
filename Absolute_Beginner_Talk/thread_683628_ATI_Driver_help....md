---
title: "ATI Driver help..."
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Gloztar on 2008-01-31
Alright, alright, I recently installed Ubuntu Gutsy after learning about a new windows emulator for it, however I have an ATI Radeon X1950Pro graphics card and can't get the driver to install without my X Server constantly crashing. I downloaded the .run file from ATI's website but have no idea what to do with it, so it's just been sitting on my desktop, can someone help?

---

### Post by Scarath on 2008-01-31
Move the file to you home folder.

Press Ctrl + Alt + F1 to get to a console with no X (installing graphics drivers works best without X) 

Then go:

```
sudo sh ./driver name
```

and that should start the install, after its done just go:

```
sudo startx
```

and it should work

good luck

---

### Post by Gloztar on 2008-01-31
Well, I'm pretty sure that worked! ... except I think I'm still having problems with my XServer... it's been crashing and it HAD been due to the restricted driver...

---

### Post by jan quark on 2008-01-31
if you are using xclient as the session which you can choose during the login

the perhaps try to install 

xserver-xgl

and select xclient session during login

---

### Post by Gloztar on 2008-01-31
Well, I had to reinstall Ubuntu to get my X Server to stop crashing, the driver on ATI's website didn't work either, does anyone know of a working one for the 1950X Pro card?

---

### Post by overdrank on 2008-01-31
> **Gloztar said:**
> Well, I had to reinstall Ubuntu to get my X Server to stop crashing, the driver on ATI's website didn't work either, does anyone know of a working one for the 1950X Pro card?

Hi and you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Gloztar on 2008-01-31
It worked! The driver is working and the X Server isn't showing any signs of crashing, thank you very much!

---

### Post by Bluestick on 2008-01-31
i have ATI X 850 PRO  and still no drivers just using the regular system drivers.... :(

 However i do have my visual effect working? not sure whats going on does that mean my Video drivers are working or what?
 when i tried enabling the restricted drivers, all hell broke loose no visual effects nothing!!!

---

### Post by kevmore on 2008-02-01
Hey Gloztar , can you get your screen into 1680 x 1024 resoulition?  What size of monitor do you have?  I have the same card, is yours agp or pci???  Mine is an agp and for the life of me I can't get it to work.

---

### Post by Crafty Kisses on 2008-02-01
> **overdrank said:**
> Hi and you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Yes, just install drivers with Envy, especially ATI drivers.

---


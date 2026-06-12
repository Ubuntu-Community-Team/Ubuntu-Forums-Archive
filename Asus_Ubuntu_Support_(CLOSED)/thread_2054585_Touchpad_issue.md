---
title: "Touchpad issue"
date: 2012-09-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by KimAndersen84 on 2012-09-07
Hi everyone
I bought a beautiful ASUS F501A and I installed an Ubuntu 12.04 64bit version on it as required by the UEFI lot. Everything works nice. I am getting used to a new environment. I migrated from KDE because of UEFI.

However, I cannot get my touchpad to work. That is, there is left click as well as able to move the pointer around. However, right click does not work. Nor does the drag and drop as well as changing the size of a window.

The synaptics drivers are up to date.

This is the files I have in my xorg.conf.d folder
10-evdev.conf             50-synaptics.conf  51-synaptics-quirks.conf
11-evdev-quirks.conf      50-vmmouse.conf    51-synaptics-quirks.conf~
11-evdev-trackpoint.conf  50-wacom.conf

I would be delighted if anyone could direct to me to a solution. I am familair with the Terminal albeit I am not an expert.

Yours truly 
Kim Andersen, Denmark (sadly do not rejoice too early about my sex. I am not a staunch Danish woman in a man's world, but a man. Kim is a typical male name in Scandinavia) :)

---

### Post by cortman on 2012-09-07
Have you tried turning it on with synclient?

```
synclient TapButton2=2
```

Then tap with two fingers to right click. Can't confirm that it'll work as I'm not at my laptop right now, but it should.

---

### Post by KimAndersen84 on 2012-09-07
Thank you for your reply. Oddly enough it works with three fingers. The drag and drop is still an issue though.

---

### Post by cortman on 2012-09-08
Hm, try

```
synclient TapButton3=2
```

you can get a list of available commands for synclient by simply typing

```
synclient
```

By drag and drop not working, do you mean you can tap on something and move your finger on the touchpad but it doesn't move what you tapped?

---


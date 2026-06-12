---
title: "white screen"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by vendetta23 on 2007-09-03
today is the first time im playing around with me ubuntu system. and i got myself into trouble a few times but i found myself out. but right now, after messing up the xorg.conf and then restoring it, my desktop is white. that is, after i log in form the normal login screen, my screen is completely white with only a mouse on it that cannot do anything. this happened before today, but was able to be fixed by using:

sudo aptitude install ubuntu-desktop.

i tried that a couple times and rebooted every time, but it just wont be fixed. please help me!

---

### Post by nowshining on 2007-09-03
i highly suggest waiting for Gutsy to come out to install as this will have better hardware support and fix many bugs so be patient. :)

---

### Post by vendetta23 on 2007-09-03
ah...

so my only option is to reinstall feisty fawn or wait for the new version?

---

### Post by overdrank on 2007-09-03
> **vendetta23 said:**
> ah...

so my only option is to reinstall feisty fawn or wait for the new version?

Hi and no you can try and reconfigure your xorg with the command
```
sudo dpkg-reconfigure xserver-xorg
``` 
and if you don't know the answer to the question then leave them as default answer given and then post back.

---

### Post by vendetta23 on 2007-09-03
haha

i did what u said but i didnt know ANY of the answers so i just left them all the way it was.

---

### Post by overdrank on 2007-09-03
> **vendetta23 said:**
> haha

i did what u said but i didnt know ANY of the answers so i just left them all the way it was.

Ok I take that statement as it returned you to the desktop GUI?

---

### Post by vendetta23 on 2007-09-03
uhh no

do i have to reboot for it to work?

---

### Post by overdrank on 2007-09-03
> **vendetta23 said:**
> uhh no

do i have to reboot for it to work?

Yes a reboot is required
sudo shutdown -r now

---

### Post by vendetta23 on 2007-09-03
rrggg

i rebooted, but i got the x error i got after i mseed with the xorg.conf trying to get my video card to work...

---

### Post by overdrank on 2007-09-03
> **vendetta23 said:**
> rrggg

i rebooted, but i got the x error i got after i mseed with the xorg.conf trying to get my video card to work...

Ok sorry to hear that you can try and run the command again and choose vesa as the driver and hopefully this will get you back to your desktop. :(

---

### Post by vendetta23 on 2007-09-03
hmm my video card seems to be fine

the driver is vesa

---

### Post by nowshining on 2007-09-03
get a gui now? or still having problems? because from the post above it seems like that you've got it all fixed up with the suggested vesa driver...

---

### Post by vendetta23 on 2007-09-03
im sorry, im bad at explaining

my driver is still vesa, but i still dont get the regular log in screen and get the x error D:

---

### Post by overdrank on 2007-09-03
disregard

---


---
title: "Duffer needs help having changed screen res and can't now log on!"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by YoYoSan on 2007-10-20
Hi Guys

Help needed to log onto my work laptop & undo whatever I did to screen res!

Having just upgraded to Gutsy on my work laptop I was trying to get my screen res right using screens & graphics munu through system > admin.

It's way wrong now because when I rebooted all I have is a very large log-in screen - I can't even log back in to return it to an unsuitable but at least workable resolution.

Any suggestions gratefully received.

Cheers

---

### Post by trjnhrse44 on 2007-10-20
[LEFT]Please do the following:
When you reach that large login screen hold down ctrl and alt and hit f2
you will see a terminal log in at the prompt,

the do the following

```
sudo dpkg-reconfigure xserver-xorg
```and hit enter
it will ask for your password, enter it and hit enter
answer the questions that follow, make sure to choose simple for screen selection, 24 bit resolution and /dev/mice for mouse selection, do emulate a three button mouse and don't pass any special arguments for the keyboard


Know you video card first so you can choose the appropriate driver when
asked if you are unsure choose the vesa driver it will work with whatever you choose but is only a basic driver to get you started
[/LEFT]

---

### Post by YoYoSan on 2007-10-20
Thanks for quick response - just about to reboot the laptop & give it a go - let you know how I get on.

---

### Post by YoYoSan on 2007-10-20
Cheers mate - worked a treat!

I now feel much more confident about having a play to see if I can get things right (having pasted that howto above the desk!):)

YoYo

---


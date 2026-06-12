---
title: "Ubuntu won't boot up!"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by smiley1213m on 2006-07-18
Ahh! My ubuntu won't boot up. It gets hung up on Configuring Network Interfaces, and goes into a Dos looking screen. I have a wireless network card in, should I take it out? Please Help!

---

### Post by Jagot on 2006-07-18
When it gets to that stage in boot press ctrl+c and it should skip the process.

---

### Post by shoot2kill on 2006-07-18
has it booted before... or is this the first time ?

when does the error come up, during boot up, or when logging in?

are you shure you installed desktop version, and not server version...

if u installed server, when the dos looking screen shows up (called terminal, or a shell in ubuntu) type

> sudo aptitude update
sudo aptitude install ubuntu-desktop

hope this helps

---

### Post by smiley1213m on 2006-07-18
Thanks! I pressed control+c, and it skipped it to boot succesfully. And to answer the other's question, the error came came up during boot up, and yes, I have booted up before. Thanks!:-D

---

### Post by shoot2kill on 2006-07-18
dont forget, you will still want to get the error fixed... no point leaving it and pressing ctrl + c every time u boot.. but sorry, i not to good with the networking ubuntu side of things... :(

---

### Post by smiley1213m on 2006-07-18
Oh geez! This is bad, after I boot up, skipping the configuring network interfaces with the control+c thingy, it loads so that I can log in, but I when it loads the desktop, the whole screen just loads up as a burnt orange colour. I can move the mouse around, but there's no menus or anything.

---

### Post by smiley1213m on 2006-07-18
Just a note to add: The screensaver works as usual, but it still has the burnt orange colour with no menus, just a mouse pointer that I can move around.

---

### Post by smiley1213m on 2006-07-18
Why won't the desktop load? I don't understand how this oculd even happen.

---

### Post by Metacarpal on 2006-07-18
To clarify: your computer used to boot to Ubuntu desktop and detected your wireless card before, but now won't do either?

If that's the case, you might need to reinstall, or it could be a sign of hardware failure.

---

### Post by kupajava on 2006-07-19
Im going with hardware issue more than likely, Ive had the same problem when my video card went bad.  Excessive bending of the cable popped the solder mounts that connect the interface to the board. Anyway, first try running the live CD of ubuntu and see if that works, that will tell you if its hardware or software.  If it works on Live CD, this could be one other thing besides hardware, do an xorg reconfigure and see if possibly your drivers have changed in some way.  A friend of mine was having the same problem and was able to boot to the command prompt with a setup cd and do the xorg config to fix it.  Just do a search on xorg and configure and you might have a little luck.

---

### Post by smiley1213m on 2006-07-22
I tdid but up before i installed dapper drake. Should I re-install. I don't have anyhting to lose on it.

---

### Post by Trizik on 2006-07-25
I'm not so sure a reinstall will fix anything. I have this exact same problem; when I boot, it hangs at "Configuring Network Devices..." and I am forced to Ctrl+C. After that, a dark orange/red background appears with a moveable mouse cursor, but that's all that ever happens. It sits like that forever... no menus, no nothing.

I could boot into Ubuntu fine before I activated my wireless Linksys WMP45GR adapter. How can I deactivate the adapter before boot?

---


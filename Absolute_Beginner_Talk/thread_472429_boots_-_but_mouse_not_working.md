---
title: "boots - but mouse not working"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by resander on 2007-06-13
System spec: Pentium III 750 MHz with 256MB RAM. 2-button, plain, new PS2 mouse
                      Installed from alternate iso distribution.

I have only just managed to get Ubuntu to boot. I can see a menubar at the top with menuitems Applications Places and System and an icon sda1 in the upper left corner of the canvas.

The mouse arrow is at the center of the screen, but does not move when I move the mouse and mouse clicks are not getting through either. The keyboard works.

This is a dual boot configuration and the mouse works for Windows XP.

As a Linux newbie I have no idea what might be the cause.

---

### Post by gn2 on 2007-06-13
Do you have a 3-button mouse to try?

---

### Post by drowner on 2007-06-13
is the mouse plugged in?

first things first

---

### Post by resander on 2007-06-13
The mouse has 2 buttons. Haven't got a 3-button mouse.

The mouse is plugged in and works when I select Windows XP on the same dual-boot PC.

---

### Post by bbarcelo on 2007-06-13
> **resander said:**
> System spec: Pentium III 750 MHz with 256MB RAM. 2-button, plain, new PS2 mouse
                      Installed from alternate iso distribution.

I have only just managed to get Ubuntu to boot. I can see a menubar at the top with menuitems Applications Places and System and an icon sda1 in the upper left corner of the canvas.

The mouse arrow is at the center of the screen, but does not move when I move the mouse and mouse clicks are not getting through either. The keyboard works.

This is a dual boot configuration and the mouse works for Windows XP.

As a Linux newbie I have no idea what might be the cause.

If you have another mouse to try out (either PS2 or USB), try booting into Ubuntu with that. If that mouse works, then I'd have to guess it's some hardware incompat. with Ubuntu if you say it works in Windows just fine. You could always try doing a Google search for your mouse's model number + linux and see what kind of results you get.

---

### Post by resander on 2007-06-13
The mouse model number is:  A4 tech OK-720.

I googled with that as key and got several matches. 

One was to what appeared to be an online store in Poland called SKLEP.linux.pl. They advertised this mouse, so it is likely it works with linux.

Haven't got any other brand of mouse, but will try to find one.

If I have to buy, what popular mouse brands work with Ubuntu 7.04?

Is there anything else I can try?

---

### Post by Pizzarth on 2007-06-13
just pull the plug out and put it back in after it loads

---

### Post by Brendan Hart on 2007-06-13
try configuring it, when i configured my monitor it came up with stuff about keyboard mouse etc,

```
sudo dpkg-reconfigure xserver-xorg
```

try that and configuring it, leave the stuff you dont know as default, thats what i did for my monitor and it came out good, then when it asks u if its 3 button mouse go 2 button

---

### Post by freesitebuilder on 2007-06-13
If you're using Feisty (7.04), there are two mouse bugs that are being investigated:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194) (ps2)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84762](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84762)

---

### Post by resander on 2007-06-13
I tried Pizzarth suggestion 'pull out the plug and put it back after reload'. It did not work.

While waiting for canvas and menubar to appear I noticed that Ubuntu was outputting a mouse arrow even though the mouse was unplugged at that point. It first appeared for about a second and then disappeared and reappeared after another second. I don't know if this is significant.

---


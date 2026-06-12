---
title: "Mouse will not work in Ubuntu"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by FuMangChu on 2007-06-17
My mouse will not function at all in Ubuntu. I am trying to install it and am at the point that i have to icons on the desktop: install and samples. However my Microsoft Optical mouse 2.0 will not work. It is fine in XP. Is there any way around this? Do I need a new mouse? Thanks guys!

---

### Post by wpshooter on 2007-06-17
What version of Ubuntu are you installing ?  Is this mouse PS2 or USB ?  Have you tried different ports if it is USB ?

---

### Post by FuMangChu on 2007-06-17
i am installing feisty (7.04) and it works in windows so i didnt think it would be the port. I tried another port anyway, and still no worky...

---

### Post by reset3x on 2007-06-17
When you change from port to port you may need to reboot.... I have that problem with my laptop... Try that and see if it works..

---

### Post by FuMangChu on 2007-06-17
No dice. Would a different mouse answer my problems? If so what kind? I would prefer to just fix the one I have as I do not want to have to put money into this venture but if its what I gotta do...

---

### Post by silkstone on 2007-06-17
I use a MS Optical Mouse 1.1A that comes with a cheapo Media Keyboard + Mouse package, and that runs fine from the PS/2 port under Feisty. I prefer PS/2 because it doesn't tie up a USB port, but I seem to remember that it didn't want to work on USB.

---

### Post by reset3x on 2007-06-17
From the live CD desktop a hit ctrl-alt-f2.. At the command line type lsusb... See if your mouse is listed.... You can then hit ctrl-alt-f7 to get back to the desktop....

---

### Post by FuMangChu on 2007-06-18
When i do that i get Bus 001-003 with 002 being listed twice. They all have ID 0000:0000 at the end of them except for Bus 002 Device 002 has ID 0471:0110 Philips after it. Which is my stereo. So no, no mouse. What do I need to do to fix this?

To anyone else who is having this problem I navigated with the keyboard to accessibility and was able to enable  my number pad to move the mouse with 5 as clicking. However I would still like to have my mouse functional so for me this is just a temp fix.

---

### Post by reset3x on 2007-06-18
Go into your bios and see if you have options for usb legacy support and usb mouse and keyoard support... Enable them it you have those options and see if that helps.. If not you may want to go out and buy a usb/ps2 adaptor... They're inexpensive and would be alot cheaper than buying a new rodent....

---

### Post by FuMangChu on 2007-06-18
so pardon the newbiness but that adapter will fix my problem? I have 2. I just had no idea that was the solution.

---

### Post by reset3x on 2007-06-18
No pardon required... We were all in you boat at in time or another...;)  If you have the usb/ps/2 adaptor that came with you mouse give that a whirl.... It would save you some headaches....

---

### Post by FuMangChu on 2007-06-18
My greatfulness to you is bested only by my hate for my stupidity. =D>

---

### Post by reset3x on 2007-06-18
I'm sure when you get things running you'll want the ATI drivers... Go here [http://albertomilone.com/](http://albertomilone.com/) and download Envy.... It's a deb package... just double click on the file and it will install... You'll find the Envy listed in Applications/System Tools.... Envy makes it all a piece of cake....

---


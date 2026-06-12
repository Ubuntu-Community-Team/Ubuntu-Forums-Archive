---
title: "xorgconfig will not work"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Metta on 2006-04-21
Hi 
Complete Newbie 

I have Toshiba Sat Pro 2100 (Cel 1.5hmz) I emailed a friend who uses breezy and asked him how do change  my screen refresh rate settings, as I have just installed Ubuntu and the screen is flickering a lot! 

 He replied saying:

[INDENT]Sounds like you need to edit your xorg.conf file.  The easiest way to do that is to launch a terminal (the black monitor-like icon) and type "sudo xorgconfig". 
The "sudo" bit tells the machine that you want to execute a command with root privileges, so it'll then ask you to enter your password (just your normal login password).  (If you don't do the sudo bit, it'll either tell you you can't run this as a normal user or you'll get right to the end of the reconfiguration routine and then find you can't save it!)

Then just answer the questions and at the end it'll rewrite your xorg.conf file.
 You then need to restart X (the graphics server part of linux), which you do by pressing Ctrl-Alt-Backspace all together.  Then it all goes scary and all you have is white text on a black background.  If it's waiting for you to login again, then just enter your username & password as normal.  But then all you have to do is type "startx" and you'll get back to your desktop.

If you reconfigured things correctly, you shouldn't have any flicker.  If you still have problems, you can either repeat the process or edit your xorg.conf file directly in a text editor but we'd better save that for another episode...!![/INDENT]

However when I type in [COLOR="Red"]sudo xorgconfig[/COLOR] I get: command not found 

I have tried other alternatives, but still no luck.

Can you help

Cheers dhamma

---

### Post by bollix47 on 2006-04-21
Try:

sudo dpkg-reconfigure xserver-xorg

---

### Post by Metta on 2006-04-22
Thanks for the advice. It worked, but then I had millions of options, which I worked through, but when I re-booted the laptop, I just got a blank screen. So I reloaded ubuntu.

Thanks

---


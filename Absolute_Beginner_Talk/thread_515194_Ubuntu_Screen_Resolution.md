---
title: "Ubuntu Screen Resolution"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by philip793 on 2007-08-01
Hello Ubuntu People,

I have just installed Wubi 4 GB and I was able to boot Ubuntu on my computer. I know how to change the screen resolution in Ubuntu. The maximum screen resolution it is 800x600. I have a monitor that supports 1280×1024 resolution. My graphics card is nVidia GeForce 6100. On my Windows OS the resolution is 1280x1024 but on ubuntu its only 800x600 and that is the maximum. Please help. BTW I am liking Ubuntu really great OS. I am a 14 year old geek.

[CENTER]:confused::confused::confused::confused::confused::confused::confused::confused:[/CENTER]

---

### Post by Rocket2DMn on 2007-08-01
This problem seems to be coming up a lot today:
Screen resolution problems are quite common, run the following command (in terminal):
```
sudo dpkg-reconfigure xserver-xorg
```
You use TAB to move around and SPACEBAR to select/enable when appropriate.  When you get to the resolution page, you should select your monitor's max resolution and everything less.
Afer the configuration is done, hit CTRL+ALT+BACKSPACE to restart the X server.  You should now be able to select the correct resolution.

---

### Post by bugster on 2007-08-01
Hi Philip

Just some words of encouragement though I can't help personally.  I had just the same problem and lived with it for some months then I asked on here. The answer came within minutes so hang in there :)

---

### Post by Tux Aubrey on 2007-08-01
Welcome philip793

Have you enabled the Restricted Drivers? (under the System>Administration menu).  That should get the right driver installed and give you the choice of resolutions that your card is capable of.)

(nVidia can be be a bit of a pain but totally workable. I have 1940x1600 res working great with a similar card)

---

### Post by MacMonster on 2007-08-01
Rocket2DMn's advice worked great for me using my ATI Mobility 9600.

PS: Only just installed Ubuntu for 1st time today. :)

---

### Post by Brindled on 2007-08-01
yeah, this worked for me too. Rocket's right about it coming up frequently. today was my lucky day.

ps. for those not in the know (like me), the CTRL+ALT+BACKSPACE command will reboot the OS. so make sure you save any work you maybe doing when trying this. ;)


> **Rocket2DMn said:**
> This problem seems to be coming up a lot today:
Screen resolution problems are quite common, run the following command (in terminal):
```
sudo dpkg-reconfigure xserver-xorg
```
You use TAB to move around and SPACEBAR to select/enable when appropriate.  When you get to the resolution page, you should select your monitor's max resolution and everything less.
Afer the configuration is done, hit CTRL+ALT+BACKSPACE to restart the X server.  You should now be able to select the correct resolution.

---

### Post by Rocket2DMn on 2007-08-01
> **Brindled said:**
> ps. for those not in the know (like me), the CTRL+ALT+BACKSPACE command will reboot the OS. so make sure you save any work you maybe doing when trying this. ;)

It doesn't reboot the OS, just the X-server (and hence any GUI programs you had running under it).  I often forget to warn people about that, sorry.

---

### Post by Brindled on 2007-08-01
> **Rocket2DMn said:**
> It doesn't reboot the OS, just the X-server (and hence any GUI programs you had running under it).  I often forget to warn people about that, sorry.

no worries about the restarting... and i almost edited my post to reflect that it wasn't necessarily the OS restarting. to newcomers, or at least myself, that's what it seems like. 

i definitely know something major restarted when i had to login again. 

linux has been good therapy for me lately.  thanks for your help, and everyone else's.

---

### Post by philip793 on 2007-08-01
[center]OMG thanks a lot tux aubrey it totally worked! Rock on dude/dudette!
:guitar:[/center]

---


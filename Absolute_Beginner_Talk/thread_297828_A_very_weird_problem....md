---
title: "A very weird problem..."
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by deusdies on 2006-11-11
Hi guys, I am new to linux (have been using win for 5 yrs) and 1h ago i've installed ubuntu. Installation process went fine, expect with a LITTLE problem; during an installation, mouse light went off (on my 7th sense STAR optical mouse). I pluged in/out the cable and light went on for a few secs, and then off again. 

During the boot of ubuntu, light also goes off.

The WEIRD thing is that the buttons work fine in ubuntu.Both buttons work (haven't tried wheel yet) but I cannot move cursor.

Mouse is on ps/2 port.

Same mouse on WinXP works perfectly fine.

Thanks,and I hope you will come out with a solution,
regards

---

### Post by JayTee on 2006-11-11
If you can boot Ubuntu then at the Grub menu choose recovery mode. You'll be in terminal mode. Type this: sudo dpkg-reconfigure xserver-xorg and hit Enter
Follow all the prompts that try to identify your graphics card, keyboard and mouse. During the portion that asks about your mouse select the PS2 option. Then type sudo shutdown -r now and Ubuntu will restart. When the Grub menu comes up boot normally and then see if you get mouse activity.

---

### Post by deusdies on 2006-11-11
I did as you said, a configuration menu came up, but I wasn't asked to choose PS2 mouse ; everything there related to mouse was "to emulate 3rd button" and "to (turn on aguess) scroll wheel)" After that, setup continued to video modes etc. 

And light is still off.

---

### Post by bulldog on 2006-11-11
Well maybe now is the time to buy your self a new mouse.

Did it work with the live cd or did you use the alternate.
Did your mouse worked when you installed ubuntu?

It's a fact not all the hardware is supported,maybe you've just ran out of luck.

{don't unplug a PS2 device from a running computer,it can damage your PS2 port!!}

---

### Post by stream303 on 2006-11-12
One possibility if you want to go into your bios setup, is to toggle the mouse port "legacy" option and see if that helps it to be recognized.  Careful!

---

### Post by kinematic on 2006-11-12
happened to me once too with a mouse from trust....it just wouldn't work on linux.
so i bought a cheapo mouse from sweex and never again had any problems.

---

### Post by seshomaru samma on 2006-11-12
Are you using Ubuntu Dapper or Edgy?
Does the mouse work with the Live CD?

---


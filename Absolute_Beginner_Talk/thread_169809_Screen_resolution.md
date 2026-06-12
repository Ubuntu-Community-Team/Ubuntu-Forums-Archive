---
title: "Screen resolution"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-03
I'm running Ubuntu 6.06 Beta Livecd and I want to modify my screen resolution but in the screen resolution preferences I only got 2 choices: 640x480 and 800x600, but when i edit de file xorg.conf in the graphic card configurations i see more screen resolutions that i'm allowed to choose.Can you help me?

---

### Post by Jeroen Vernooij on 2006-05-03
[QUOTE=kart3r]I'm running Ubuntu 6.06 Beta Livecd and I want to modify my screen resolution but in the screen resolution preferences I only got 2 choices: 640x480 and 800x600, but when i edit de file xorg.conf in the graphic card configurations i see more screen resolutions that i'm allowed to choose.Can you help me?[/QUOTE]

Hi, 
What kind of graphics card do you have? I have the same problems with my Intel GMA 950 graphics chip.

---

### Post by kart3r on 2006-05-03
I think that's a 3D Rage II+ 215GTB [Mach64].I already thought that could be because i'm running a livecd and he does not allow me to choose more screen resolutions but i'm not sure :S

---

### Post by Jagot on 2006-05-03
[QUOTE=Jeroen Vernooij]Hi, 
What kind of graphics card do you have? I have the same problems with my Intel GMA 950 graphics chip.[/QUOTE]

You may need to force your graphics card with 915resloution which is available in the repositories.

I'm afraid I don't know about your card kart3r

---

### Post by kart3r on 2006-05-03
Allright then, thanks anyway =) i keep looking ^^

---

### Post by Jeroen Vernooij on 2006-05-03
kart3r, are you sure this isn't a graphics-card limited issue? 
Are you coming from Windows? 
If so, was 1024x768 supported in Windows?

---

### Post by Jimmey on 2006-05-03
Try 
> dpkg-reconfigure xserver-xorg

Then, when it asks about the monitor recognition thing, say no. Then select advanced. It'll eventually face you with some dialog for selecting the appropriate resolutions. Press space on the ones you want to enable ( 800 x 600, 1024 x 768, etc ). Then..Restart X, if you can on the liveCD ( I'm not too sure. ) Hopefully then you'll have a bigger choice.

---

### Post by Jagot on 2006-05-03
Well I can tell you that, providing your card supports them, which I assume it does, it shouldn't be because it is the live CD that you cann choose other resolutions - I have an Nvidia 5200 and it gave me my correct resolution without having to do anything.  Maybe you need to install drivers, but that will be best done in an install rather than the live cd.

---

### Post by kart3r on 2006-05-03
Jimmey it did not worked :x but answer this, if I install ubuntu in place of running the livecd do i still have this problem?

---

### Post by kart3r on 2006-05-03
i've made it xD jimmey it works finnaly, the problem was with the monitor, i think that the refresh rate was to high and then I can't choose an higher screen resolution but now it's lovelly hehehehe thks a lot m8

---


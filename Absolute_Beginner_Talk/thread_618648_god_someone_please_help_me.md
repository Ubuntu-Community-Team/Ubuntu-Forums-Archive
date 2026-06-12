---
title: "god someone please help me"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by the cooke on 2007-11-20
hello everyone, i have a presario v2000 v2720wm laptop with a dual boot up i have windows xp and Ubuntu gutsy gibbon install on it. the main problem is the graphics card, a ati radeon express 200m and when ever i try to fix my graphics card when i start up and select Ubuntu, the whole computer just crashes and i cant even start up windows because is says that it has a system startup error. it also say that it has a microcode error so if that is related just tell me.oh yeah just because that im a completely new at using Ubuntu i would greatly appreciate it if only the people who don't guess but  are completely sure of themselves help me, because if anything goes wrong then i have to completely start over again and reinstall windows. if anyone can help me i would probably be beyond thankful

---

### Post by magicfab on 2007-11-20
In order to be "completely sure", we'd need exact error messages. Could you please provide that ?

---

### Post by markharding557 on 2007-11-20
can you be more specific about where it crashes,ie at grub menu or later,does ubuntu boot up before it crashes

---

### Post by the cooke on 2007-11-28
it starts when i enable my graphics card then i restart and it trys to enable itself but then it just crashes and completely destroys itself

---

### Post by santiagoward2000 on 2007-11-28
> **the cooke said:**
> it starts when i enable my graphics card then i restart and it trys to enable itself but then it just crashes and completely destroys itself

Hi!
I have the same graphics card and never experienced anything like this. Do you get any error message when you install the drivers, or after you reboot your system?

---

### Post by the cooke on 2007-12-01
well it started when i tried the new operating system gutsy gibbon because i could never get it to work with feisty fawn. but when i enabled it through the restricted drivers it automatically installed it and then it told me i need to restart so i restarted and than it gust collapsed on itself. so i said screw it and i decided to just reinstall windows and Ubuntu and just use windows for the serious stuff and play with Ubuntu, but then i got bored with Ubuntu and decided to turn here to see if i could fix it without completely destroying it again.

---

### Post by SunnyRabbiera on 2007-12-01
hmm, it might be best to get the settings for xorg from the liveCD and see if you can patch it...

---

### Post by monte48lowes on 2007-12-01
Write this down and boot into 'Recovery Mode'

```
dpkg-reconfigure -phigh xserver-xorg
```

This will reconfigure xorg.conf to get you back to a working desktop.

Mike

PS. This command is in the xorg.conf file. I have left out sudo, since booting into recovery mode brings the computer to a command line as root.

---

### Post by the cooke on 2007-12-01
thanks dude that actually helped a lot but it still didn't work and what does sunnyraberia try to be just a little more simple for me please

---

### Post by PmDematagoda on 2007-12-01
Try this in Recovery mode:-

```
dpkg-reconfigure xserver-xorg
```

And select the driver as vesa. After reconfiguration, do:-
```

startx
```

---

### Post by the cooke on 2007-12-03
alright i tried that but all it says when i start in Ubuntu and type in startx is:
fatal server error:
server is already active for display 0
if this server is already running remove /tmp/.X0-lock and start agian

oh yeah when i start up i have to press alt & F4 for my computer to start running and it says that there is a error with the drier 8139cp and that i should try 8139too

and one more thing i greatly appreciate all the help iv'e gotten already

---

### Post by shuttleworthwannabe on 2007-12-03
I have had a similar experience with my HP Compaq nw8240 ATI fireGL V5000 graphics card;

During the dpkg-reconfigure xserver-xorg reconfiguration, when you come across selecting the possible resuolution for your screen, select ones that apply to you; a safe bet would be to check what the max resoultion is in Windows, and select that option. What I do is also select 1024x768 (as this for me is the native res for my screen). Also choose the graphics card carefully: for me this was fglrx, and NOT the ati (that was my problem actually).

Hope you come right, good luck.

S

---

### Post by the cooke on 2007-12-08
still doesnt work

---


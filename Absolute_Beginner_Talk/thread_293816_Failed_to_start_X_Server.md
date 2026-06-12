---
title: "Failed to start X Server"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by wabsrck on 2006-11-05
Alright so I am a complete Linux noob and was really excited when I got my ubuntu 6.06.1 LTS disks in the mail. So I stuck it in thinking that this would be way to easy to be true and......it was. I got the boot screen and clicked the boot/install or whatever. It started loading things and then it gave me this error "Failed to start X server(your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem <YeLinux Ubuntu 2.6.15-26-386#1PREEMPT

and lower down it says...

-bush:no job control in this shell
To run a command as admin(user "root", use "sudo<command>" See man sudo_root for details.

I can't press enter on ye(which im guessing is yes cut off)

Please remember I am a noob at this so I don't know how to put in code and such...yet

](*,)

---

### Post by %hMa@?b&lt;C on 2006-11-05
when you get dropped to a  console enter
```
sudo dpkg-reconfigure xserver-xorg
```
follow the prompts

---

### Post by wabsrck on 2006-11-05
When I do that I follow the prompts(not knowing what to do with half of that and then get to where it says xserver disabled...then I restart and it does the same thing...


Also what should I put for xserver driver...I am using a GeForvve FX 5200 OC

---

### Post by CatKiller on 2006-11-05
When running from the live ("Desktop") cd, none of the changes that you make are stored anywhere - it's a risk-free way to see what it's like. So restarting the computer will get you back in the state you were in before. **Ctrl-Alt-Backspace**, however, restarts the X server without having to restart the computer. (Well, technically it kills the X server, but hopefully it will start again)

You should pick either **nv** (an open source driver for nVidia cards) or **vesa** (a very generic driver that should work on anything, with limited features).

---

### Post by wabsrck on 2006-11-05
ok so I tried that and got stuck on the bit color step in the process...upon pressing enter it took me to the command line and said:

xserver-xorg postinst warning: overwriting possibly-customised(let me break in here and say yes it is spelled wrong in the code) configuration file; backup in /etc/x11/xorg.conf.20061105205645
ubuntu@ubuntu:~$

the ctrl-alt-bckspc didn't work at all

i tried the startx command and it said:
Fatal server error: no screens found

---

### Post by wabsrck on 2006-11-05
Any assistance would be nice...so this is basically a bump

---

### Post by CatKiller on 2006-11-05
From what other people have said, I think that the bit depth step is the last one. The configuration gets written to the file, and the configuration utility exits.

```
nano /var/log/Xorg.0.log
``` will let you look for any obvious error messages to tell you why you've got no screens. It's a bit scary-looking.

```
nano /etc/X11/xorg.conf
``` will let you see how you've configured X.

Did you try both the nv and vesa drivers? Hopefully someone who knows more about it than I do will be able to help you.

---


---
title: "Calling all NVIDIA 8800 owners"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by mortuk on 2007-05-02
Hey all

Been trying to get ubuntu working on an NVIDIA 8800 for a couple of weeks without success. I have an 8800 GTS in my work machine, and a GTX in my home machine and having the x server crashing issue on both.

I have tried under both Edgy and Feisty and no joy :( Followed loads of forum threads regarding this problem, but none seem to work so I don't know if its user error (most likely) or what. I can get x working in the 'vesa' and 'nv' drivers, but the 'nvidia' ones dont wanna play ball.

Anyways I have decided its best to start from scratch with a fresh install, and try to get some direction from other people who have had and solved the same problem.

I am desperate to f**k off XP from both my machines and get down with some Linux action, plus Cedega and Beryl are calling out to me, so if anyone could lend a hand that would be much appreciated!!

---

### Post by starcraft.man on 2007-05-02
Ok, I believe I've already talked to a few people who got the 8800 to work so that shouldn't be a problem. Just to be clear, you previously did have a good install when you were using the vesa and nv drivers, its only when you had the nvidia on, that being the case I guess there was an install issue.

Did you get an error message when your xserver crashed? Or did the gdm just fail when you booted and you were at terminal?

Anyway, if your doing a clean install this shouldn't be too hard. Make sure firstly you do all updates to Feisty or Edgy (either should work, Feisty is fairly stable in my experience). After getting up to date, try the [Envy script]("http://www.albertomilone.com/nvidia_scripts1.html"), it should take care of installing the nvidia driver and configuring your xorg. Just donwload version 0.9.2 debian, double click it to install. After its installed go to Applications > System Tools > Envy. Then click automatically install nvidia driver, say yes to any request to install applications in the terminal, then yes to reconfigure xorg and reboot. If this doesn't work then please try to give a specific error message so we can diagnose it.

I'm a 6800 GT owner, Nvidia usually works lets hope we can fix your problem :)

---

### Post by mortuk on 2007-05-02
have had lots of different errors, but yes basically on the install it would goto start x and crash, give me a gdm / no screen error, then go blank. Press ctrl + alt + f2 and brings me a terminal, edit the Xorg.conf to change to vesa or nv and x works, but obviously if I want proper grapics acceleration to game or use Beryl I need the nvidia drivers working

I tried envy before, though that was in Edgy. Did the same thing really with the X server. Don't know if I need to do anything about the restricted drivers before I install with envy.

when I get home (too busy in work at mo) I'll have a go with envy and see how it goes and let you know :D

---

### Post by mortuk on 2007-05-03
Sweet, don't know what I did differently but it worked! Might have been the fresh install but envy worked fine, had a few problems configuring xorg.conf but sorted that, install beryl, sorted :D

Nice one!

---

### Post by graylion on 2007-05-10
could you post your xorg.conf please?

---


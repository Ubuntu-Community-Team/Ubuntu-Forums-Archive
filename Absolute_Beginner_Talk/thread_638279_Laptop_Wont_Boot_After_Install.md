---
title: "Laptop Wont Boot After Install"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by prodigalson666 on 2007-12-11
Installed gutsy on my acer 5520, after reboot the bar freezes on the usplash and doesnt go any where. I rebooted and pressed alt-f2 to go into verbose mode, the reboot freezes at the reboot usplash screen resolution, it freezes on the 1280x1024, I did not choose this resolution during install, I used the alternative cd and choose 1280x800, the laptops native resolution. Booting into safe mode reproduces the same results.

At the grub menu, press "e" to edit the normal boot entry, scroll down to the line that begins with "kernel" and press "e" again. Remove the words "quiet splash" from the end, press enter to save, and "b" to boot. This will give you a no nonsense verbose mode. Is it hanging up in the same places, if at all? If it boots just fine, it is probably a known issue with your usplash resolution, check out the attached link.

I tried this suggestion but the same results.

ok after 3 min of being frozen I get this screen

busy box v1.1.3 (debian 1:1.1.3-5ubuntu7) built ion shell (ash)
enter help for a list of built in commands

(initramfs)

This is a re thread but I haver not received any more replies and this is very important, but beyond my experience, any ideas anyone? 
__________________

---

### Post by meborc on 2007-12-12
this is wierd :S ... i would try to do a reinstall with livecd, just to see if it gets different results... it seems something went totally wrong with the first install

---

### Post by mitran on 2007-12-12
I have the same problem !  ( do not yet know how to make a new theard . 
so i am useing youers hope you er not mad. 
I did have Ubuntu 7.04 runing on my ps3 , and did a uppdate to 7.10 now when i boot , it boots i hit henter at the Kboot promt it starts .
But after a few seconds my PS3 goes "bip,bip" and shuts down. 
( if i stay in Kboot) nothing hapens , then it hits me lol  i have the wrong i do have the wrong Kernel installd ! so is ther a way for me to install the Kernel "linux-cell" from Kboot ? or do i have to reinstall Ubuntu 7.04 ?   ( i am as you see a linux noob )

---

### Post by prodigalson666 on 2007-12-12
No please join along, this is very annoying. The live cd works, I've installed twice with 7.10, debian and mandriva, all debian, all the same results!!!

---

### Post by beniwtv on 2007-12-12
Hey prodigalson666,

Can you post the exact lines when it hangs (with the quiet and splash options removed)?

Does it always hang at the same places?

---

### Post by prodigalson666 on 2007-12-12
either before the edit or after I get the same message'
busy box v1.1.3 (debian 1:1.1.3-5ubuntu7) built ion shell (ash)
enter help for a list of built in commands
(initramfs)

It hangs at 1200x1080 resolution, which is out of my laps range, so I installed with the alternate cd, chose the right resolution and received the same message. Open suse and sabayon both work fine, the only other issues with all the distros I installed was the sound, but that is another problem all together. I would prefer to use ubuntu. The one consistant factor with the boot up problem is it occurs with debian based distros, I tried ubuntu, mandriva, debian, mint, all stop at the same spot. I even tried fiesty, same occurance. thanks

---

### Post by Sims2789 on 2007-12-12
Try booting into terminal mode and type *sudo dpkg --configure*, and reset the resolution when prompted to. I don't know how to boot into the terminal, though.

---

### Post by prodigalson666 on 2007-12-12
Berkeley CA! Home of unix I bet! Awesome!
I'll try thanks, let you know tomorrow!

---

### Post by MuSlIm on 2008-03-21
**_[COLOR="Red"]Do this an it will work, i have same problem>[/COLOR]_**
When you turn on computer and when boot many comes don't run anything just 
```
[B][COLOR="Blue"]1. press "e" 
2. Press "e" key again
3. now write "all_generic_ide."
4. press "enter"
5. and last one press "b" and computer will reboot, then u can use your new OS!!!!![/COLOR][/B]
```

Say THANKS!!!

---


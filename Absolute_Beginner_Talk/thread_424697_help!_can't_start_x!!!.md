---
title: "help! can't start x!!!"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by gdsaar on 2007-04-26
hi!

i started really using ubuntu over a month ago, after trying a bunch of different liveCDs.

i recently upgraded to feisty fawn.

and i thought about updating my nvidia drivers.

i went to synaptic and got the newest ones, entitled, "nvidia-new" or something like that


but when i installed it and restarted x, it crashed! now i can't boot ubuntu with a gui. it just comes to a command prompt login. i removed that driver, but idk what else to do. i have no idea how to edit an xorg file or whatever its called. i'm willing to learn tho! can someone tell me what's wrong? it gives me an error that no screens are being found.

tried that ubuntu repair mode thing, didn't work.

also, if this helps....my graphics card is the nVidia GeForce MX 440 AGP 4X/8X. apparently my card is notorious for something. dunno what, though.

---

### Post by kosmic on 2007-04-26
In the command line type this :

```
sudo dpkg-reconfigure xserver-xorg 
```

and follow the steps, and you should have X again ;)

---

### Post by Seisen on 2007-04-26
Put this in the terminal and follow the prompts

```
sudo dpkg -reconfigure -phigh xserver-xorg
```

---


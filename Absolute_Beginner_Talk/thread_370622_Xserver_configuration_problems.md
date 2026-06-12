---
title: "Xserver configuration problems"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Torahteen on 2007-02-25
Ok, I'm rather new to linux. I'm doing a dual boot with Windows XP and Ubuntu. Using the alternative CD, I installed Ubuntu Drapper Drake. Now, I'm following a guide to install, and it says that it's very common to have Xserver not work the first time, and that you have to configure it, which I am trying to do. Well... I think the problem starts with the fact that it won't detect my nVidia GeForce FX5200, and will only detect the built in Intel card that came with my Dell Dimension 3000. So I'm asking you guys... how do I get this set up!?

---

### Post by STREETURCHINE on 2007-02-25
you will probably have to install the nvidia driver to get the vidio card to work,

as to the xserver 

    ```
sudo dpkg-reconfigure  xserver-xorg
```

follow the prompts and answer the questions

restartx   ctrl>alt>backspace

---

### Post by StarscreamD on 2007-02-25
You can also try to setup your bios to use your onboard card via initial install. This is what I had to do, because the install recognized my onboard chip as my primary video adapter. So I just jacked the monitor into my initial monitor port on my computer during the seup process. That way, I could at least get X to boot up. I then did all my configuration on my video setup that way, rather than struggling with command line.

Hope that makes sense. :)

---

### Post by bodhi.zazen on 2007-02-26
I would install the nvidia driver.

IMO the best way is with the envy script

See here : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Torahteen on 2007-02-26
I was already using dpkg-reconfigure xserver-xorg, which is where it wouldn't detect my nvidia card (I selected the nv driver, but it wouldn't give me my card). Could I just have it get set up to use my built in card, and install the other screen while in the GUI? If so, how do you set up a card in the GUI?

---

### Post by bodhi.zazen on 2007-02-26
Install the nvidia driver from envy

Then, in a terminal, type 

```
nvidia-settings
```

---

### Post by Torahteen on 2007-02-26
I'm sorry... envy?

---

### Post by bodhi.zazen on 2007-02-26
Look up, at my first post, follow the link I gave you.

Envy  is a python script to install the nvidia driver.

(I user the "unstable" version without any problems and this is a newer driver and I would advise you go with it :) )

the opensource driver (nv) apparently does not play well with your card :(

---

### Post by Torahteen on 2007-02-26
Ok, btw. I tried to at least get into the GUI so I could set up my internet (its wireless, and the install couldn't figure it out), so I configured XServer to run using my other card (the one it DOES recognize), but I can't get the computer to start up using the other card. It's not using it, so XServer still will not work...

I'll try envy, but does it require I have internet? I do not have internet on Ubuntu at the moment. Perhaps there's a way I can download it in windows and run it from my FAT32 partition?

---

### Post by Torahteen on 2007-02-26
Well I'll be... this is wierd. I accidentally rebooted, and... it went into the GUI! :D Yay!

---

### Post by SuperAndy on 2007-03-15
if i could bring this topic back from the partial dead...

xserver wouldn't work at all without some playing around. when i use either the ati or vesa drivers, with my monitors native resolution, i get no output. my monitor shows no signal input...

the only point i can see having a problem is the PCI address. i have run lspci -x | more, and it seems that the address is correct, but i cannot be sure.

PCI:3:0:0 is what it says

---


---
title: "Quick Probably dumb question frustrating me..."
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by DUNC4N on 2007-05-19
After entering "nv" how do I save and close? So I can go on to the next step, er issue ;)

I'm following this from [http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html]("http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html")

[I]The restricted drivers manager has made things a mess for a lot of people with newer and older nVidia cards.The restricted modules are getting load priority over the nvidia-installed module.

If you want to fix this follow this procedure

sudo apt-get install build-essential

sudo apt-get install xserver-xorg-dev

sudo vi /etc/default/linux-restricted-modules*

Change the DISABLED_MODULES=”" to DISABLED_MODULES=”nv”[/I]

I can't figure it out, and everyone assumes that baddies like me know all the little commands.

I've been trying to install the 8800 drivers for a couple days, with no luck. Searching and trying, searching and trying.

Anywhoo, here is my status

Nvidia drivers still not installed, resolution not right need 1680x1050

Thanks much for any advise.

My goal: If I can play counterstrike, and fold under ubuntu64 when I'm not playing, everything else I know I can do under ubuntu.

Woot, fingers crossed ;)

---

### Post by sad_iq on 2007-05-19
Change the line that says : ```
sudo vi /etc/default/linux-restricted-modules*
``` 
with : ```
sudo nano /etc/default/linux-restricted-modules*
``` then to save press Ctrl+X then Y then Enter to save!!! (I've only changed the editor from **vi** to **nano**...nano is more newbie friendly)

---

### Post by raja on 2007-05-19
Nano is a more beginner friendly editor to use from the shell. To use it instead of vi, just do
```
sudo nano /etc/default/linux-restricted-modules*
``` and after changing what you want to, hit Ctrl-x to quit.

---

### Post by Kobalt on 2007-05-19
You can use nano or any other text editor to do this, for example : > 
sudo nano /etc/default/linux-restricted-modules*
Use Ctrl+X, then Y and Enter to save and quit.

---

### Post by DUNC4N on 2007-05-19
Sweet thanks much :)

Rebooting

---

### Post by DUNC4N on 2007-05-19
Well after reboot, still same situation, fail to start x.

This is getting so frustrating.

The only way I can boot is  still replacing the quiet splash, with quiet noapic

after typing automatix-nvidia-restore, which really seems like it does nothing.


GRRRRR.....:mad:


There has to be someone thats got x64 running with nvidia drivers, and at 1680 x 1050, smoothly.

I would appreciate, any further assistance. 

-dunc4n

---


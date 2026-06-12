---
title: "nVidia driver install killed Ubuntu"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Hairyred on 2006-07-25
I have attempted to install nVidia driver as instructed [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-20c0b7106f06055eed889efe3946f560c34a8b1a") but something has gone wrong and I was presented with the terminal screen. A fix to revert to the backup config file was given as 
'cp /var/backups/xorg/xorg11.conf.2006-07-26-13:06:57 /etc/x11/xorg.conf'
I entered this set of commands but it doesn't work. I may have some of the spaces between the instruction wrong, but I can't check it because it broke! I did write it down but my eyes ain't as good as they used to be. HELP!

---

### Post by Hairyred on 2006-07-26
From an earlier post;
"GeForce4 mx440 requires nvidia-glx, when in fact it requires nvidia-glx-legacy. "
How do I now install the correct driver? I installed the glx as stated on this site but I have the mx440 card.

---

### Post by KaeseEs on 2006-07-26
To quickly get your system's GUI working again:

```
sudo dpkg-reconfigure xserver-xorg
```

... and choose 'nv' as your driver.

Once your stuff works again, run the following:

```
sudo aptitude remove nvidia-glx
sudo aptitude install nvidia-glx-legacy
sudo nvidia-glx-config enable
```

This should get everything working.  ( As a side note, I have an nVidia geForce 2 MX 400, and the regular nvidia-glx drivers work for me, whereas the nvidia-glx-legacy drivers don't.  Funny world. )

---

### Post by VexD on 2006-07-26
OK.. umm i have GeForce 4 MX and i tried this and sofar so good but when i put sudo nvidia-glx-config enable it get..  

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


And idk.. im about to reboot and see what it does..

I need this fixed because im stuck on 640x450 and it wont change!! If someone has an awncer to this plz help

---

### Post by Hairyred on 2006-07-26
I've done the sudo dpkg-reconfigure xserver-xorg and it's back to how it was. I tried to install new drivers using
sudo aptitude remove nvidia-glx
sudo aptitude install nvidia-glx-legacy
sudo nvidia-glx-config enable
but I couldn't get the last line to work, so I am leaving it as is until I do an upgrade in a week or two.
Many thanks for your help.

---


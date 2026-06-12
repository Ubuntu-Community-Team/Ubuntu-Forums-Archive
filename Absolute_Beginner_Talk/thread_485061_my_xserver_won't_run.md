---
title: "my xserver won't run"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Mostlyharmless42 on 2007-06-26
I just installed Nvidia drivers through envy and now my xserver won't start up

I tried using this code to reset my xserver:

[INDENT]**sudo cp /etc/X11/xorg.conf_backup_200706261327 /etc/X11/xorg.conf**[/INDENT]

I pressed enter and it didn't give me any messages so i told the system to reboot and it didn't fix anything

It also keeps displaying this error message, sometimes in the middle of the lines i am typing

[INDENT]**[ 306.900622] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.**[/INDENT]

Each time it displays the error the number in the brackets changes.
help me please

---

### Post by rocknrolf77 on 2007-06-26
Try ```
sudo nvidia-xconfig
```

or ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then ```
sudo /etc/init.d/gdm restart
```

---

### Post by bodhi.zazen on 2007-06-26
This is not a problem with the nvidia driver, but rather seems related to your network card.

I do not have a solution, just some links with similar solutions :

They seem to suggest that **bcm43xx-fwcutter** needs to be installed.

Try ```
sudo apt-get --purge bcm43xx-fwcutter
sudo apt-get install bcm43xx-fwcutter
```

[http://www.linuxquestions.org/questions/showthread.php?t=467164](http://www.linuxquestions.org/questions/showthread.php?t=467164)

[https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/97682](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/97682)

[http://www.debianhelp.org/node/7608](http://www.debianhelp.org/node/7608)

HTH

---

### Post by Mostlyharmless42 on 2007-06-26
> **rocknrolf77 said:**
> Try ```
sudo nvidia-xconfig
```

or ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then ```
sudo /etc/init.d/gdm restart
```

Your second solution worked when i switched my driver from nvidia to nv, except when i tried to turn on desktop affects it had to enable the accelerated driver and i had to switch it back to nv again to get my xserver to work.  I was running the affects just fine before....

The second thing apparently had nothing to do w/ my xserver, but installing that package made my wireless work which i've been working on for half a week now, so you are now my new hero:D

---

### Post by rocknrolf77 on 2007-06-26
Just had a problem of my own with envy. Try running envy again from the commandline.

First to kill the x server : ```
sudo /etc/init.d/gdm stop
```

Then log in and do a : ```
sudo envy -t
```

Hope this works for you too :)

---


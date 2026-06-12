---
title: "Ahh! help!!"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Morph89 on 2007-08-01
Okay, I dunno what I did. When I boot into Ubuntu through Grub now, all I get is black and white text. It asks me for my username and then password and after I sign in it just stays in a b/w command-line mode. How do I revert back into my regular Ubuntu desktop??

 I messed around with some audio settings after looking at my topic on getting my integrated soundcard to work (here: [http://ubuntuforums.org/showthread.php?t=513504&highlight=no+audio+integrated](http://ubuntuforums.org/showthread.php?t=513504&highlight=no+audio+integrated) )

I think the last command I entered was a re-installation of ALSA, 

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

That was the last thing I entered before I rebooted my comp and found I was unable to access the regular Ubuntu GUI.

Please help me get back into my regular desktop!

---

### Post by weresheep on 2007-08-01
Hello,

Once you have logged in via the text mode, the below command should start the normal GUI...

```
startx
```


If the GUI doesn't start and/or you see error messages then its possible your X Windows configuration is broken and will need more help (from someone who knows about that stuff).

First things first though. See if that command brings up the GUI?

-weresheep

---

### Post by PriceChild on 2007-08-01
Please```
sudo apt-get install ubuntu-desktop
```You have removed gdm among other things :)

---


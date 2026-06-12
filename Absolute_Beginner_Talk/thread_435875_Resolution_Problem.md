---
title: "Resolution Problem"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-05-07
Hi

I wondered if someone could help with a resolution problem I have. 
At the moment I'm running 1280 x 1024 which is okay but I recently bought a new monitor running 1680 x 1050. I wondered how I can increase the resolution to run at it's best.
I had a look in the xorg.conf file and noticed it's still listing my old monitor under 'screen'  with various resolutions going up to 1280 x 1024. How can I get ubuntu to recognise my new monitor and update the possible resolutions.
My graphics card is a geforce 6200.
Everything works fine under XP so I know my card is able to do it.

Many thanks

gazzadtfan

---

### Post by Kobalt on 2007-05-07
Hello,

If the resolution you want is not in xorg.conf, type in a Terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the spacebar and then validate with Enter. Restart your X with Ctrl+Alt+Backspace and it should be ok.

---

### Post by Praill on 2007-05-07
:S

I dont know if id recommend a dpkg-reconfigure xserver-xorg, especially if youve done any manual configuration on you xorg.conf. It will erase everything.

Simply go to the device section and add the modes you want for the default depth. In your case add 1680x1050.

---

### Post by Wiebelhaus on 2007-05-07
[Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

give that a shot , then configure using the nvidia control panel under system tools.

---

### Post by John.Michael.Kane on 2007-05-07
You can the method outlined here.
[http://ubuntuforums.org/showthread.php?p=2605716#post2605716](http://ubuntuforums.org/showthread.php?p=2605716#post2605716)

---

### Post by Kobalt on 2007-05-07
Oops, I had forgotten the* -phigh* option in my command... I should sleep from time to time I guess.

---

### Post by alienexplorers on 2007-05-07
If you run nvidia settings start it with [COLOR="Red"]gksudo nvidia-settings[/COLOR]  This lets you modify the xorg.conf file with the new settings.

---

### Post by gazzadtfan on 2007-05-07
Thanks folks for all your suggestions. 

I now have it running the way it should be.

Thanks again.

gazzadtfan

---


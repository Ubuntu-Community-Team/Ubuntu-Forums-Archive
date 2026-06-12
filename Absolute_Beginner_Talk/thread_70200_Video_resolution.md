---
title: "Video resolution"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by jeff grant on 2005-09-29
I'm  new to Ubuntu and to Linux, though by no means new to Windows - so I hope I'm posting this in the appropriate place. If I'm not doubtless someone will advise me. I've installed Breezy Badger. In principle I'm impressed and like it very much. I'd love to be able to happily migrate from the Gates empire. But can any one who knows about these Linux things tell me why, in a system which includes a 64mb Abit Siluro graphics card, an Athlon 2400 processor, 512mb RAM and a Dell Trinitron monitor capable of 100mhz refresh rate the refresh-rate adjuster will allow me to set it only at 60hz??? It's unusable. Word processing is like watching a flickering old time movie. I'm sure there's a way and I just don't know it. Any help would be gratefully appreciated. Thank you. Jeff

---

### Post by NZ-Wanderer on 2005-09-29
Not figured out where to change refresh rates myself, but dropping my resolution down from what Breezy set it to (1280x1024) down to 1152x864 automatically changed my refresh rate from 60 to 75 :) :)

---

### Post by jeff grant on 2005-09-29
[QUOTE=NZ-Wanderer]Not figured out where to change refresh rates myself, but dropping my resolution down from what Breezy set it to (1280x1024) down to 1152x864 automatically changed my refresh rate from 60 to 75 :) :)[/QUOTE]
Many thanks. I'll try it right now  (I have a dual-boot on this computer) and will come back with result. Though as I write I have a feeling I tried this and I was given no alternative to the original setting the same as yours - 1280x1024. We'll see.

---

### Post by heimo on 2005-09-29
If you could attach your /etc/X11/xorg.conf file (use the attachments button on forum editor), it could help. You probably need to reconfigure this file. Your monitors exact model could help too. It's sometimes as simple as running this on terminal / console (read all of this message before proceeding):

```

sudo /etc/init.d/gdm stop (this will close your graphical user interface)
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup (makes backup)
sudo dpkg-reconfigure xserver-xorg (starts reconfiguring, asking questions)
sudo /etc/init.d/gdm start (to start graphical user interface again)
``` 
You need to pay attention to questions about your monitor and graphics card.

If you mess up, you can go back to old configuration with
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm start (to start graphical user interface again)

``` 
Some of this information may be helpful:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")

Please post back your information, xorg.conf and monitor model and we can give you more specific instructions. In that case you don't need to do reconfiguring, we can hopefully give you the exact changes to that configuration file.

---

### Post by jeff grant on 2005-09-30
[QUOTE=heimo]If you could attach your /etc/X11/xorg.conf file (use the attachments button on forum editor), it could help. You probably need to reconfigure this file. Your monitors exact model could help too. It's sometimes as simple as running this on terminal / console (read all of this message before proceeding):

```

sudo /etc/init.d/gdm stop (this will close your graphical user interface)
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup (makes backup)
sudo dpkg-reconfigure xserver-xorg (starts reconfiguring, asking questions)
sudo /etc/init.d/gdm start (to start graphical user interface again)
``` 
You need to pay attention to questions about your monitor and graphics card.

If you mess up, you can go back to old configuration with
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm start (to start graphical user interface again)

``` 
Some of this information may be helpful:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")

Please post back your information, xorg.conf and monitor model and we can give you more specific instructions. In that case you don't need to do reconfiguring, we can hopefully give you the exact changes to that configuration file.[/QUOTE]
Many thanks for that. I'll give it a go. I won't be able to get back to you until the beginning of next week as I'm away from the weekend in an hour or two from now. But thank you once again.

---


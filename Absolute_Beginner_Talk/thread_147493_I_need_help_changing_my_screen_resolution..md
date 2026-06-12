---
title: "I need help changing my screen resolution."
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by nala on 2006-03-20
Fixed! :) These forums are awesome.

----------------------------------------------------------------------------------------------------------

I downloaded updates for Ubuntu yesterday. (I'm not sure which updates - or how to find out what they are. ) My screen resolution was fine before the update, but now it's stuck on 640x480. How do I fix this? I already tried system>preferences>screen resolution.

---

### Post by mr.p on 2006-03-20
[QUOTE=nala]I downloaded updates for Ubuntu yesterday. (I'm not sure which updates - or how to find out what they are. ) My screen resolution was fine before the update, but now it's stuck on 640x480. How do I fix this? I already tried system>preferences>screen resolution.[/QUOTE]
I think there would be a few thousand threads on this so try using the search function. :p 

But anyways, run the following command and then do CTRL+ALT+BACKSPACE to restart the X server.

```

sudo dpkg-reconfigure xserver-xorg

```

The above command will give you the option to choose some resolutions.

---

### Post by meborc on 2006-03-20
may be some of these threads give help: [http://www.ubuntuforums.org/search.php?searchid=4400187](http://www.ubuntuforums.org/search.php?searchid=4400187)

---

### Post by wjp.reg on 2006-03-20
[QUOTE=nala]I downloaded updates for Ubuntu yesterday. (I'm not sure which updates - or how to find out what they are. ) My screen resolution was fine before the update, but now it's stuck on 640x480. How do I fix this? I already tried system>preferences>screen resolution.[/QUOTE]

```
Ctrl-Alt-F1
sudo /etc/init.d/ gdm stop
sudo dpkg-reconfigure xserver-xorg
```
select your video card, etc.

restart gdm
> sudo /etc/init.d/gdm start
or reboot

Cheers!

---

### Post by wjp.reg on 2006-03-20
[QUOTE=nala]I downloaded updates for Ubuntu yesterday. (I'm not sure which updates - or how to find out what they are. ) My screen resolution was fine before the update, but now it's stuck on 640x480. How do I fix this? I already tried system>preferences>screen resolution.[/QUOTE]

```
Ctrl-Alt-F1
sudo /etc/init.d/ gdm stop
sudo dpkg-reconfigure xserver-xorg
```
select your video card, etc.

restart gmd
> sudo /etc/init.d/gdm start
or reboot

oops, slow on the trigger :)
Cheers!

---

### Post by nala on 2006-03-20
Thanks everyone. I'll let you know how it goes when I get home. Sorry for not searching first. iw as a bit panicked. n.n;;

---

### Post by nala on 2006-03-20
[QUOTE=mr.p]I think there would be a few thousand threads on this so try using the search function. :p 

But anyways, run the following command and then do CTRL+ALT+BACKSPACE to restart the X server.

```

sudo dpkg-reconfigure xserver-xorg

```

The above command will give you the option to choose some resolutions.[/QUOTE]

It works even better now than it did before. Thanks for your help! :)

---


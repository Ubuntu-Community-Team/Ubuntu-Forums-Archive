---
title: "[SOLVED] 2nd Screen Please HELP"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by remali on 2008-04-04
Greetings, 
I have Gutsy on my laptop and choose in System-> Administration-> Screen & Graphics the 2nd screen. The system asked to reboot and I restarted it. After that it loads but I can't see the login screen. Please help me.. I did reconfigure the xorg but nothing. 
Though the led that shows the wireless connection seems to work. So I think that I can't see the login screen because I have chosen 2nd screen. How do I undo that?????

Thanks in advance

---

### Post by Amarsingh0793 on 2008-04-04
Something similar happened to me once but I only have 1 screen. I did some config thing on Screens and Graphics and it mucked up my screen settings. To fix it, I had to check if my right graphics card was selected in Screens and Graphics. If that doesn't work, try reinstalling your graphics card's restricted drivers.

Good Luck :)

---

### Post by remali on 2008-04-04
Thanks for the reply,
but the problem is that I can't login in ubuntu.. I just get a black screen. Is there any way to do this in console?????

---

### Post by remali on 2008-04-04
Does anyone know in which file are the settings from Screen & Graphics options are stored?? And how to change them??? :confused: :confused: :confused: :confused:

---

### Post by Amarsingh0793 on 2008-04-04
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=650835](http://ubuntuforums.org/showthread.php?t=650835)

---

### Post by remali on 2008-04-04
I tried everything on this post but nothing seem to work ](*,)

Now when I open it, it doesn't even show me the black screen.
It gets crashed in "Running local boot scripts (/etc/rc.local)"
Argggg.... Is there anything I can do???

---

### Post by alexsabree on 2008-04-04
I don't know any of the solutions off the top of my head.. but there is always the option of getting all of your data that you need off your ubuntu instalation and then reinstall ubuntu. :mad:

---

### Post by Amarsingh0793 on 2008-04-04
Does your Recovery mode still work?

---

### Post by remali on 2008-04-04
I finally did it.  
I reconfigured xorg
```
 sudo dpkg-reconfigure xserver-conf
```

but this time I added

```
startx
```
(starts gnome)

after the configuration..
And it worked....:guitar:
Thank you guys for the replies :biggrin:

---


---
title: "Graphics glitch on install?"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by Adrnshw6 on 2006-04-06
Hi everyone, I am completely new to Linux, and decided to try ubuntu.  I downloaded the DVD .iso for 64 bit AMD processors (which I have), partitioned my hard drive correctly, and then burned the DVD.  I booted up the DVD and everything was fine until I have to choose my desired resolution.  I pick 1280 X 960 (this is what I use in Windows) and then a mouse shows up with a greenish brown background.  This this appeared:  [[IMG]http://img112.imageshack.us/img112/7519/p10100415uv.th.jpg[/IMG]](http://img112.imageshack.us/my.php?image=p10100415uv.jpg)

Anyone know what that is and how to solve my problem?

Thanks!

---

### Post by taurus on 2006-04-07
I recommand you go with a lower resolution first, 1024x768, and once you get it working, install the right driver for your video card and increase the resolution after that.  By the way, what video card do you have on your AMD machine anyway?

---

### Post by Adrnshw6 on 2006-04-07
I have a 7800 GT.  My processor is a X2 4200 +.  Thanks for the advice, I'll try it in the morning and post back.

---

### Post by taurus on 2006-04-07
If you still can't get it to work, you can always get into a console with (holding down) <Ctrl><Alt>F2.  Log in and edit your /etc/X11/xorg.conf and change the driver from whatever it is to nv or even vesa...
```

sudo nano /etc/X11/xorg/conf

```
Look for the section that looks something similar to this...
```

Driver                       "vn"

```

---

### Post by tmahmood on 2006-04-07
I heard there are some problems with 64bit version of Linux. so why don't you try the 32 bit version? I am running ubuntu dapper 32 bit verison. 

now about your problem. can you post the content of xorg .conf file? 

@taurus

they should be

```

sudo nano /etc/X11/xorg.conf

```

and 

```

Driver       "nv"

```

---

### Post by Adrnshw6 on 2006-04-07
Ok, I typed in "sudo nano /etc/X11/xorg.conf" and I get to this screen that says GNU nano 1.3.8 at the top, with all different possible commands at the bottom, such as ^G, ^W, ^U, etc.  The middle of the screen is black, nothing about display.  What do I do?

---

### Post by taurus on 2006-04-07
Wait for it to boot up completely.  Then, press <Ctl><Alt>F2 to get to a console.  Then, log in with your userID and password.  You will be dropped into a prompt (like the DOS one in Windows) and that's where you type in
```

sudo nano /etc/X11/xorg.conf

```
Use the down arrow to scroll down until you get to the section about your video card and replace whatever it is with either nv or vesa.
```

Driver               "nv"

```
Then, <Ctl>x to save it (as it says at the bottom of the screen) and y to save it as /etc/X11/xorg.conf.  Probably best to reboot at this point and see if your screen still messes up again.  If it's still, then change the Driver to "vesa" and reboot again!!!

p.s.  ^X means hold down <Ctl> while pressing x...

---

### Post by Adrnshw6 on 2006-04-07
Ok, I typed that exact line, and the screen showed up nothing.  No files or words whatsoever to browse through.  Here is a small video I made:  [http://www.youtube.com/watch?v=gwIajgAsl9M](http://www.youtube.com/watch?v=gwIajgAsl9M)

---

### Post by Adrnshw6 on 2006-04-07
Anybody?

---

### Post by taurus on 2006-04-07
[QUOTE=Adrnshw6]Anybody?[/QUOTE]
What is the output of this command (from a terminal) then?
```

ls -la /etc/X11 <-- capital X, not x!!!

```

---

### Post by Adrnshw6 on 2006-04-07
Typed it in annd it says "```
ls: /ect/Xll: No such file or directory
```"

---

### Post by taurus on 2006-04-07
[QUOTE=Adrnshw6]Typed it in annd it says "```
ls: /ect/Xll: No such file or directory
```"[/QUOTE]
That would be capital x and number eleven as in X11, NOT Xll (capital x and letter l)!!!

---

### Post by Adrnshw6 on 2006-04-07
[QUOTE=taurus]That would be capital x and number eleven as in X11, NOT Xll (capital x and letter l)!!![/QUOTE]

Oh damn, that was it.  Those damn I's look so similiar to 1's in code.  Thanks for being so helpfull.

It was already "nv" so I changed it to "vesa" and saved.  It worked!  Thanks so much for your help!

---

### Post by taurus on 2006-04-07
[QUOTE=Adrnshw6]Oh damn, that was it.  Those damn I's look so similiar to 1's in code.  Thanks for being so helpfull.[/QUOTE]
No problem at all.  And yes, l looks real close to 1.  ](*,) 

> It was already "nv" so I changed it to "vesa" and saved.  It worked!  Thanks so much for your help!
Now, you want to install "nvidia" driver for your video card so you can get some nice graphics with 3D acceleration.  Here is a link for you so read it and follow the instructions in there.  If not sure, you can always post back!

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---


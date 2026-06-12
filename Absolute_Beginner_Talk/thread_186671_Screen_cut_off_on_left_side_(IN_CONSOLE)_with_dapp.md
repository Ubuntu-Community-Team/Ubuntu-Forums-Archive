---
title: "Screen cut off on left side (IN CONSOLE) with dapper"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by dan_99503 on 2006-06-02
NO X installed, running server install from console. 

I am missing one character on the left side and my monitor and I cannot adjust far enough to make it visable. It's an LCD with a VGA connector and I noticed it's running at 70Hz and not at 60Hz. I'm not sure if thats the problem but I would like to set it to 60Hz to see if the problem goes away.

I have searched everywhere but I cannot find any information on how to set the refresh on boot to resolve this problem with the console without any luck.

Thanks, 

- Dan

---

### Post by confused57 on 2006-06-02
I'm having the same problem:

[http://www.ubuntuforums.org/showthread.php?t=186370](http://www.ubuntuforums.org/showthread.php?t=186370)

---

### Post by jhull99 on 2006-06-09
I'm having a similar problem, but on my monitor the text runs off of the bottom of the screen.  Changing the monitor settings doesn't really help, I can adjust the monitor so I can see the top of the text, or the bottom, but I can't shrink the screen enough to show both at the same time.  The refresh rate is set to 70 Hz instead of 60, like above, and for some reason the resolution is 640x350.  My monitor is a Princeton LCD 1510.  Any help would be greatly appreciated.

---

### Post by xXx 0wn3d xXx on 2006-06-09
[QUOTE=dan_99503]NO X installed, running server install from console. 

I am missing one character on the left side and my monitor and I cannot adjust far enough to make it visable. It's an LCD with a VGA connector and I noticed it's running at 70Hz and not at 60Hz. I'm not sure if thats the problem but I would like to set it to 60Hz to see if the problem goes away.

I have searched everywhere but I cannot find any information on how to set the refresh on boot to resolve this problem with the console without any luck.

Thanks, 

- Dan[/QUOTE]
In terminal type:
> sudo nano /boot/grub/menu.lst
Look for a line like
> quiet splash
Try adding vga=789 to the end of it makeing it look like this:
> quiet splash vga=789
If that doesn't fit your monitor, experiment with different vga resolutions.

---

### Post by jhull99 on 2006-06-12
That worked great!!

Thanks,

Jonathan

---

### Post by brentoboy on 2006-06-12
I used vga=791
that gives me higher resolution and fixed the original problem, 
thank you xXx 0wn3d xXx

---

### Post by dan_99503 on 2006-06-18
vga=791 solved my problems as well. Thanks!

---

### Post by AlexLee on 2008-03-06
tried the solution but nothing happens
not even after restarting x

---


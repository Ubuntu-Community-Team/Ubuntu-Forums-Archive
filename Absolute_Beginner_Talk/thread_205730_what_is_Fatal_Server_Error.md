---
title: "what is Fatal Server Error"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by rmaier on 2006-06-28
Fatal server error:
failed to initialize core devices
X10: fatal 10 Error 104  (connection reset by peer)  on x server ".0.0"
/usr/bin/startx:line 169  /dev/mull: Permission Denied

also tells me (EE) xf86Openserial:cannot open device no such file or directory
error oening /dev/wacom : Success

the above repeats about 5 times..... 

prior to this I have tried to reconfigure xserver-xorg ..this sent me to the video driver, selected nv, and enter, it then goes thru several lines ending with the above....when I reboot the computer it goes through all the ubuntu initial screen, stops at x server. and i get the command line user@ubuntu~$
where I entered the code to reconfigure stated above.

Ubuntu 6.60 tty1

got to be a way to get through this to begin using the computer again...thanks for help.....#-o

---

### Post by nalmeth on 2006-06-28
Instead of the 'nv' driver try the 'vesa' driver, and then from inside install nvidia's proprietary driver.

---

### Post by rmaier on 2006-06-28
okay typed the sudo dpkg-reconfigure -phigh xserver-xorg   then it went to the choose the X Driver  ....highlighted vesa  pushed enter and got the 
xserver-xorg postinst warning: overwriting possibly customized configuration file; backup in /etc/X11/xorg.conf .20060628220915

and back to the user@ubuntu~$ command line 

I entered start x and the series of fatal server error X10 came up with the same user@ubuntu~$ command line.....

if you have ideas on how to help they are much appreciated..

is there a way to set my Bios to read the motherboard cd to restore the system, or should I have it read the Ubuntu disk, or just leave it alone and follow suggestions!!!!

---


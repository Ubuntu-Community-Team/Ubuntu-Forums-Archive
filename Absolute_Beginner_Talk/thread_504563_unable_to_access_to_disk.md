---
title: "unable to access to disk"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by pasomad on 2007-07-19
I guys
help me
I installed ubuntu, great
but when I go on terminal and I try to enter in a mounted disk or in a directory blu colored it said it dosesn't exist even if I write ls and it shows me that there is (but it's blu colored)
whY ?
thanks in advance

---

### Post by taurus on 2007-07-19
What directory you want to access/change from a terminal and what command do you use (any error message when you run that command)?

```
ls -la 
```

---

### Post by pasomad on 2007-07-19
it's  /dev/disk
and in terminal it appears blu and any blu directory that I try to open it says "no such file or directory"
tahnks a lot

---

### Post by taurus on 2007-07-19
What happens when you run

```
cd /dev/disk
```

---

### Post by Ayuthia on 2007-07-19
Have you tried using /media/disk instead of /dev/disk?  Normally, you cannot access a device.

---

### Post by pasomad on 2007-07-19
yes I tried cd /dev/disk
and also cd /media/disk
but it says always "no such file or directory" but when I type ls I see it (blu colored ) !!!!!!

---

### Post by taurus on 2007-07-19
Can you post the output of this command then?

```
ls -la
```

---

### Post by pasomad on 2007-07-20
typing ls -la it appears
drwxr -  xr -x   2     root    root   220  2007 - 07- 19 08:21 [COLOR="Blue"]disk[/COLOR]

what does it mean ?

thanks for your help

---

### Post by pasomad on 2007-07-20
I explain you why I need to access to disk (hd ntfs windows)
I want to execute this command 
[SIZE="2"][SIZE="1"][I][I][COLOR="SeaGreen"]"
Once ubuntu boots and the gui finally comes up, hook up the USB drive you copied the 6gb image to. A window should pop up showing the contents of the drive. Take note of where its mounted. It should be /Devices/Yourdrivesvolumename

6. Open a terminal window and cd to that directory (/Devices/Yourdrivesvolumename). Do an “ls” to make sure you are in the right place (you should see the 6gb img file.

7. In the terminal window type:

[SIZE="3"]**dd bs=1048576 if=./tiger-x86-flat.img of=/dev/hda**[/SIZE]

Replace hda with the correct drive! If you only have one drive, its probably hda. Thats what mine was. You are about to erase this entire drive so make sure youve got it right and make sure you want to do this! 
"[/COLOR][/I][/I][/SIZE][/SIZE]
from the directory where I have my ***.img file but I can access from the terminal to this directory
Is there another way to execute correctly this command ?
thanks in advance

---


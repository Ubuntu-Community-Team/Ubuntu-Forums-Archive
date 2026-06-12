---
title: "files from cd and slow Firefox"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Stephen47 on 2006-12-12
How do I get files from a cd into my /home folder. Firefox seems very slow compared to when I run it in Windows. Why  is this? I thought Linux was supposed to be faster. Also how can I change my screen resolution? Everything looks distorted. I have a wide screen on my laptop and the only resolution to choose when I open screen resolution preferences is 1280 x 1024 any hellp would be appreciated, thanks

---

### Post by xyz on 2006-12-12
Hi,
First of all...are you trying to customize Dapper or Edgy?

Also go [H E R E]("http://www.ubuntuforums.org/search.php?searchid=11067779")
you'll find HowTo's FF,Swiftbox...and check out Leightweight Gnome, Disable IPV6, Enabling Pre-Link and more.
Good luck! Let us know how it goes!

---

### Post by Kobalt on 2006-12-12
To get other resolutions avaliable you must open a Terminal and type this command line : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Pick the resolutions you want avaliable by pressing the **spacebar** and then restart Xserver with Ctrl+Alt+Backpsace. 
Re login, and here you go !

---

### Post by Stephen47 on 2006-12-12
I am trying to get my bookmarks from windows to firefox in ubuntu. I burned them to a cd but now what?

---

### Post by xyz on 2006-12-12
The simples way is to drag/drop your file to your desktop.
Open FF > Organize Bookmarks > File > Import > Click on desktop

---

### Post by Stephen47 on 2006-12-12
how do I see the files on the cd?

---

### Post by Henry Rayker on 2006-12-12
if the cd doesn't automount (it will pop up on the desktop if it does), you'll need to mount it.try ```
mount /mnt/cdrom
``` in the terminal.

---

### Post by meng on 2006-12-12
Actually I think the default mountpoint for the cdrom is
/media/cdrom

---

### Post by Henry Rayker on 2006-12-12
GAH! you're right.

```
mount /media/cdrom
```

My computer at work is running RedHat and the default mount point is /mnt/cdrom on our installation. Sorry about that!

---

### Post by Stephen47 on 2006-12-12
I got the files from the cd and my bookmarks are in place.Thanks for the help with that. I still have the screen resolution problem. I entered sudo dpkg-reconfigure -phigh xserver-xorg in the terminal and thsscreen flickered and then a dos like prompt came up and it restarted ubuntu with no changes.

---

### Post by xyz on 2006-12-13
Hi Stephen,
"heimo" wrote a quite complete guide; you may want to read on it here:
[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?p=454217")
Let us know how it goes!

Just a little advice: see how the title of your thread reflects 1 problem (files from cd and slow Firefox) when, in fact, you're asking 2 questions within the thread: FF + screen resolution.
In order for people to help you better, try and label your title to reflect 1 problem at a time. Also...other members/visitors may have a "screen resolution" problem and it helps them find a solution.
Thanks.

---

### Post by Stephen47 on 2006-12-13
does an lcd display have a refresh rate?

---

### Post by meng on 2006-12-13
Yes, most commonly it is 60 Hz. Google your make/model if you want to be sure. It is common that if your RR is set at 75 Hz, the LCD will refuse to show it!

---

### Post by Stephen47 on 2006-12-13
Yes it is 60 Hz but the ubuntu resolution is 1280x1024 whereas in windows it is 1680x1050 how do i get that in ubuntu? The type isn't as crisp nor is it really black it is sort of gray.

---


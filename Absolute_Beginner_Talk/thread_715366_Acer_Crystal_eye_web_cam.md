---
title: "Acer Crystal eye web cam"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Naqash on 2008-03-04
Hi guys, i have Aspire 5720 laptop, i have installed ubuntu 7.10, but its crystal eye web cam is not working, i have installed comorama web cam viewer and Cheese, when i run cheese web cam's light on top of my computer turns on, but gives no output.

 some good members of ubuntu community on orkut helped me and asked me to download these files...

# Makefile
# dynctrl.txt
# svn-version.sh
# uvc_compat.h
# uvc_ctrl.c
# uvc_driver.c
# uvc_isight.c
# uvc_queue.c
# uvc_status.c
# uvc_v4l2.c
# uvc_video.c
# uvcvideo.h

after downloading i ran the svn-version.sh file i got some new files along with Module.symvers, it is zero byte file and i dont know how to run it, anybody can help me here.?

---

### Post by El French0 on 2008-03-05
I have the same problem, can't seem to get the Acer Crystal Eye webcam on my extensa 4620z.....
It doesn't help that I'm a linux n00b though...

---

### Post by punong_bisyonaryo on 2008-03-05
Can you type in terminal "lsmod" and see if the uvcvideo module is listed there? If your webcam uses the Linux USB Video class (uvcvideo), then you're out of luck with v4l2 apps like cheese, wengo, and other v4l1 applications (see [related article here]("http://antirez.com/m/p.php?i=169")).

Try to run Ekiga. Go to Edit > Preferences, and under the video settings set your webcam to use v4l2 and report back here with your results.

---

### Post by Naqash on 2008-03-06
This is the output of "lsmod"

[http://www.shortText.com/fkdzvw](http://www.shortText.com/fkdzvw)

it shows that
uvcvideo               57480  0 

Then I ran Ekiga, and I changed its setting to V4L2, my web cam's green light turns on but the  screen of Ekiga only shows a green screen as output.

---

### Post by Naqash on 2008-03-15
Ekiga looks like this

[[IMG]http://img292.imageshack.us/img292/7716/screenshotkw1.th.png[/IMG]](http://img292.imageshack.us/my.php?image=screenshotkw1.png)

---

### Post by natirips on 2008-03-15
Try these files (I used them to install my Crystal Eye Webcam on Acer Aspire 5520) (and they aren't zero-byte:))

---

### Post by natirips on 2008-04-29
> **natirips said:**
> Try these files (I used them to install my Crystal Eye Webcam on Acer Aspire 5520) (and they aren't zero-byte:))

Usage notes:

- download the files to your desktop
- extract the files (right-click the icon and click extract here (or something like that, I'm not sure since I have localized version))
- open console (ALT+F2 (to run a program) than enter "gnome-terminal" without the quotes)
- now go to your Desktop directory from console: "cd ~/Desktop" (without the quotes again, mind the capitalisation/case and notice that it might be called something else if you have a localized (non-english) version, type "ls" in console to check up - it will list all non-hidden directories and files there are)
- now go into the linux-uvc directory: "cd linux-uvc", or what ever it is called if you renamed it
- now enter the following commands:```
./svn-version.sh
sudo make
sudo make install
```It _should_ be installed now, unless you got some errors/mistakes in the proccess (or I wrote something wrong). Try restarting if it's not working. If it's not working after a restart, there's some problem. Possible causes might be: you have a diffrent webcam from mine, you don't have build-essential package installed (you can install it throught System -> Administration -> Synaptic), something else?

---

### Post by forastero on 2008-04-29
Just finish a complete bare metal install of Ubuntu 8.04 on Acer Aspire 5920.
Crystal Eye Cam works, sound OK, wireless perfect, etc.  Super brainless installation and I have an Ubuntu laptop.:KS

---

### Post by xRes on 2008-05-19
Anyone know if the post from natirips works on Acer Aspire 5720?

---

### Post by natirips on 2008-05-19
> **xRes said:**
> Anyone know if the post from natirips works on Acer Aspire 5720?
Why not give it a try? I have noticed that those drivers do not work with ALL programs there are (i.e. Camorama), but it works with Cheese and Kopete (at least for me), and probably with some more programs. There's not really much you can lose if it doesn't work, maybe a few kilobytes to a megabyte of disk space. If you'll want to uninstall the drivers, do everything the same as you did when installing, except the last command is "sudo make uninstall" instead if "sudo make install". However, I'm not sure if it'll work because some makefiles do not support uninstallation, but most do. I haven't tried because it works for me so I have no reason to uninstall it.

---

### Post by dwrecording on 2008-07-12
> **forastero said:**
> Just finish a complete bare metal install of Ubuntu 8.04 on Acer Aspire 5920.
Crystal Eye Cam works, sound OK, wireless perfect, etc.  Super brainless installation and I have an Ubuntu laptop.:KS

MY cam works but my mic doe's not can anyone help? i have acer extensa 5420

---

### Post by natirips on 2008-07-12
> **dwrecording said:**
> MY cam works but my mic doe's not can anyone help? i have acer extensa 5420

Try playing with the source device (Mic Boost, Line in, Digital, Capture, etc...), also try shouting at it (mine's very silent (Aspire 5520G)). Other than that, I think it should work out-of-the-box.

---

### Post by jonppe on 2008-07-23
I installed those linux-uvc drivers on my Acer Travelmate 7520G.
Crystal Eye webcam is now working with Cheese and Ekiga. Anyway, I actually tried only XSane and Canorama before the installation, so I'm not sure if it was needed, after all. 
btw, Recording is also working. Page:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
has some hints. All tabs in Volume Control and the Preferences should be checked.

---


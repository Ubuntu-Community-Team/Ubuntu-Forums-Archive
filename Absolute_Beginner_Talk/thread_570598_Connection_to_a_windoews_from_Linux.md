---
title: "Connection to a windoews from Linux"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by xdarkgokux on 2007-10-08
HI, i want to play this game on my Windows Computer than is in my network. I heard you can do this through terminal services..?? like through VNC or something?? can someone plz tell me how.? thx

---

### Post by cameronw on 2007-10-08
Hi install RealVNC ([http://www.realvnc.com/products/free/4.1/index.html](http://www.realvnc.com/products/free/4.1/index.html)) on your windows computer, configure it (instructions on site) then go to Terminal on Ubuntu and type 
vncviewer -fullscreen (then IP address of windows computer) and hey presto (hopefully) windows will appear

Drop the -fullscreen option for windowed mode

---

### Post by Drakkor on 2007-10-08
Or install Crossloop on both computers, via wine in Ubuntu

---

### Post by cameronw on 2007-10-08
Would that work on WINE though. It's not in the WINE AppDB but I guess its worth a try.

---

### Post by Drakkor on 2007-10-09
Yeah, it works fine..... except the startup window is kinda messed up , but when connected , it works fine ! :)

---

### Post by darren1270 on 2007-10-09
Installed crossloop the other day.... worked great.

And it was really cool to help my friend use his windows box while I was using Ubuntu..... good stuff.

Darren

---

### Post by Drakkor on 2007-10-09
Yeah, I live in California, and use Crossloop to fix my mom's xp computer in Florida,lol :)

---

### Post by lionround on 2007-10-09
I have wine installed and configured (I hope) but I can't seem to get get Crossloop to install.

I am fairly new to Linux but am getting "pretty good" at command line, but I am not having any luck with this one.

Can anybody help?

Thanks

---

### Post by Drakkor on 2007-10-09
You should just be able to right-click the setup.exe file and "Open with Wine" to install.

---

### Post by lionround on 2007-10-09
That is an option, however when I do that, nothing happens.  I can go to /.wine/drive_c/windows and run wine regedit or wine notepad.  Those work.  But if I try to run the setup.exe, I get the following error:

wine: could not load L"C:\\Program Files\\setup.exe": Bad EXE format for 

Thanks

---

### Post by Valinski on 2007-10-09
I use gnome-rdp on my network. Its pretty simple and works great. The only problem is you cant go the other way round. But if you do go with VNC, you can also confiure that in gnome-rdp so you will have the best of both worlds. :)

---

### Post by Drakkor on 2007-10-09
Where is the crossloopsetup.exe file ?

---

### Post by lionround on 2007-10-09
It is in /home/david/.wine/drive_c/Program Files

---

### Post by Drakkor on 2007-10-09
I would try to just cut it out of there and paste it on your desktop,then try the right-click
Open with wine trick.

---

### Post by lionround on 2007-10-09
Same problem.  I pasted it both into my home folder and the desktop.

Tried the right click on both...nothing.

Tried it in terminal and got the same error (but with a different path, of course)

Is it possible that my wine is installed incorrectly??

---

### Post by Drakkor on 2007-10-09
Yeah,you could try reinstalling wine, I just right-click the setup file from the desktop,and
select Open with "wine" and it goes into setup.

---

### Post by lionround on 2007-10-09
Well, I feel like a fool.  I reinstalled wine.  Deleted the setup file and tried to re-download it from crossloop.com.  It is zero bytes.  So, I looked in the trash and the other downloads were zero bytes as well.  I can't seem to get the download unless someone has the setup file archived that they can send to me.

Thanks for all the help

---

### Post by Drakkor on 2007-10-09
Yeah, I have it and can send it to you, but I don't understand why you can't just download
it from Crossloop, it's 2.3mb , PM me

---

### Post by lionround on 2007-10-09
Drakkor,

Thanks for the offer, but I had also written Crossloop tech support and they just emailed me the latest version.

I am going to try to get this up and running.

Thanks for your help.

---


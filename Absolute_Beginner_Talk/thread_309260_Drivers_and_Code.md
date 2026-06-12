---
title: "Drivers and Code"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by spudgunner on 2006-11-29
I've been playing around a Ubuntu LiveCD and am really interested in installing it on my computer, but I gotta figure out a few things before I do... how do I install drivers for printers, webcams, wireless, etc... and where are you supposed to put in all the different code that I'm seeing all over the place?

---

### Post by 56phil on 2006-11-29
Welcome to Ubuntu. 

The only driver I had to install was a video driver from ATI. Wireless worked fine out of the box. Printer installation can be simple or a pain. It depends on the type of printer you have. I know nothing about a driver for your web cam. Sorry.

Hope this helps.

---

### Post by daniminas on 2006-11-29
The drivers come up with the linux kernel. You don't need to install it after the installation, but exist some expentions for some devices.

For printers you can check:

System->administration->Priners.. and ther you can add a lot of drivers/auto dectetc etc.

Ive an omega USB webcam, and for use it i just connect it.. and open an app like ekiga to test it..

You can check all the support for your devices from your live cd

good luke

---

### Post by jlx on 2006-11-29
If your hardware is supported by ubuntu usually it will work out of the box and you don't have to install/configure anything. In some cases you'll have to edit some configuration files and change some values, add some lines, etc. In other cases you'll have to search in internet or in ubuntu forums and cross your fingers. 
A good start is boot the livecd and see what it's working. If wireless, printer, webcam (I don't think so) it's working then it should work when you intall Ubuntu on your hard disk. If you don't want surprises the best thing you could do is write down all your important hardware (model, manufacturer, etc) and search in ubuntu wiki if they are supported. Then search through the forums and find if people has problems with that hardware. Also if you want to use linux as you main SO you can find what hardware is "linux compatible" before buying it. 
Good luck and give a try, you won't regret.

---

### Post by spudgunner on 2006-11-29
Which program you use to edit files?

---

### Post by MasterOfDisaster on 2006-11-29
A forewarning:

Some wireless devices can be tricky to install, although most all work with ndiswrapper.  Overall, most hardware is pretty well supported.

For editing configuration files, any word application will do.  Nano is good for command-line usage, and GEdit is bundled with Ubuntu.  I would recommend Leafpad (personal favourite), its available through apt-get/Synaptic.

---

### Post by spudgunner on 2006-11-29
I have a Lexmark 3350 printer, tried to print a page and it didn't work... I have a Logitech QuickCam and I tested it with eKiga, no dice there either... and I have no wireless reception where I am now anyway, so yeah... don't know about that yet

---

### Post by xolot1 on 2006-11-30
you can look at linuxprinting.org for info on specific printers and their drivers.  some printers are not supported well, but id say that most are supported to some degree.  whether or not your printer is listed there, chances are there is information about it on google.

i cant help with the webcam. sorry.

what wireless card do you have?
at the command line, type:
lspci
then look for "network controller" or the like.


willi

---

### Post by jlx on 2006-11-30
To edit files you can use any text editor. If you're using gnome use gedit.
You should search the models and manufacturers of your hardware in the forums.

---

### Post by Perfect Storm on 2006-11-30
Lexmark printers are the most "hostile" in linux, you'll be better with any other brand.

---

### Post by daniminas on 2006-11-30
I've an Omega Webcam and it works perfect, and my printer is a Lexmark Z12.. works fine too.. No wireless for me.

---


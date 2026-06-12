---
title: "Help Installing Tablet Drivers"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Saylient_Dreams on 2007-08-14
Hi, this is my first time using Linux. The distro I am currently using is Ubunto Studio, and I installed it using Wubi. First let me state what computer I have:
Gateway CX210X
-Intel Core2Duo 1.6 Ghz
-ATI x1400 Mobility
-80GB HDD
-2GB of Ram
-Finepoint Digitizer
-Sigmatel Audio
I assume those are the important aspects to know about the computer to help me out. My problem is getting the Finepoint Digitizer to recognize my stylus. I think I have everything else set up so far, getting the graphics card to work was pretty complicated for me a first time user of this.
I found a few threads that related to my problem, but I don't understand what to do, and where to do these edits and inserts
[http://ubuntuforums.org/showthread.php?t=146279](http://ubuntuforums.org/showthread.php?t=146279)
[http://ubuntuforums.org/showthread.php?t=429701](http://ubuntuforums.org/showthread.php?t=429701)
I am suppose to edit a serial.conf file, I couldn't find that, and I'm also suppose to edit xorg.conf, which I cannot find. I am totally new to how everything works in Ubuntu, if someone can guide me, or direct me to resources I can use to edit those files, that would be very helpful. Thanks for the help :D

---

### Post by Hospadar on 2007-08-14
Well your xorg.conf is located at /etc/X11/xorg.conf, and your serial.conf will be at /etc/serial.conf (make sure you install the setserial package first, or it won't be there)
The best way to get at these files would be to open up a terminal in Applications->Accesories->Terminal and enter ```
sudo gedit /etc/X11/xorg.conf
``` or whatever file you want to edit.  the sudo give you access to the files since they are system files (not user files) and gedit is your text editor.

If you would prefer to use the gui and browse to the files with nautilus, you will first want to install the package "nautilus-gksu" (this will let you edit system files without opening them from the desktop) you can either do this through synaptic (System->Adminstration->Synaptic) or you can do it in the terminal with ```
sudo apt-get install nautilus-gksu
```you'll need to restart gnome with ctrl-alt-backspace for this to load up, so do that (this will close all your programs, so don't have anything unsaved) (alternatively you could just restart the machine)

then go to Places->Computer and on the left hand side, go to "filesystem" this will take you to the root of the filesystem and from here you can navigate wherever.  To open these admin files, you'll want to right-click them and say "open as administrator"

Also, check [this]("http://www.linuxquestions.org/questions/showthread.php?t=497879") out.  And i believe that the actual file you are looking for is not /etc/serial.conf, but rather /var/lib/setserial/autoserial.conf (it gives you a command to run if you want to manually edit it, you should do that if you edit it)

---

### Post by Saylient_Dreams on 2007-08-14
This forum sure does move fast. Thanks for the info, I'll give it a try and see if I can do it. 
EDIT: Was wondering how do you extract files into the system folders. I'm trying to extract fpit_drv.so into /usr/lib/xorg/modules/input/

---

### Post by Saylient_Dreams on 2007-08-14
I'm still having trouble with this. I've edited the xorg.conf file and also the autserial.conf file that was mentioned in the 2nd post. Still my tablet isn't responding to anything. Can someone please help me out. Thank you.

---


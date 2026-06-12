---
title: "Server GUI Interface"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by tudedude on 2006-08-05
New to Linux. I just installed Server 6.0.6 on an old system to try out. Now I would like to use backuppc for automatically backing up my other Windows systems in my home network. I already have SAMBA installed and working, but apparently I will need a GUI to use backuppc as well as Apache server. 

Is it absolutely a bad thing to use a GUI on a server? Sounds like most people think you should just use a command line on a server. (security? system overhead?) 

Looking for suggestions but I am leaning on installing a GUI, unless I can be shown it is just as easy to do a backup of other windows sytems to disk without using a GUI. Thanks everyone.

---

### Post by taurus on 2006-08-05
No, it is not a bad thing to have window manager running on a server!  Depending on what window manager you want to use, here are your options:

```

sudo apt-get install ubuntu-desktop <-- for Gnome
sudo apt-get install kubuntu-desktop <-- for KDE
sudo apt-get install xubuntu-desktop <-- for XFce4

```

---

### Post by tudedude on 2006-08-05
Any pros and cons for each of those?

---

### Post by stanz on 2006-08-05
> **tudedude said:**
> Any pros and cons for each of those?

[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

GUI's...which ones...why & how's... pretty goooood! :)

---

### Post by David Corrales on 2006-08-05
Actually it's not that bad to have a GUI especially if you're not yet comfortable with the CLI.
What I would recommend though is having the system starting out directly on a console and then you log and start the desktop by typing **startx**.
This way, you can use the GUI whenever you need to but it won't eat up your resources automatically.

---

### Post by em3raldxiii on 2006-08-05
Just a quick note for other nuewbies who might be reading this:
 
A graphical inerface (such as Gnome, KDE, Xfce) may use more resources, and if your server machine is not particularly robust, this could cause a problem.  Command Line Interface installations of Linux are extraordinarily low-overhead, so are very well suited to running servers even on low-end computers.
 
On the other hand, I have found that Gnome is very effective at resource management.  If your computer is just going to be a server most of the time (ie you don't use it for routine daily computing), then having a graphical user interface running won't cause any grevious harm.
 
If you want to choose a GUI that can be used on fairly low-end computer systems, you might consider using Xfce due to it's lower resource footprint.
 
Just for reference purposes, I have a LAMP webserver running on a PIII 1Ghz with 512MB SDRam.  It has the KDE Graphical User Interface running all the time.  It's connected to my KVM switch so i can administer it directly if I need to do so.  You can check the performance:  [www.anxietyofinfluence.ca]("http://www.anxietyofinfluence.ca").  Note that I am using PHPBB for their forum (I know, some of you would groan LOL), and unless the computer recieves extra traffic (say, 4 users all streaming their songs simultaneously), users don't typically notice any serious performance issues.
 
Hope that helps :D

---


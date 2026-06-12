---
title: "Can't Connect To Internet!"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-08-26
OH WHY ME!!:confused: 

Now I can't get Kubuntu to connect to the internet!  Last night when I shut down everything was going well, but this morning when I booted I just can't get on line.  I rebooted, still nothing.  I checked my connections, nope!  Windows works OK (thats how I am getting this done). I checked in the connections section and the DCHP seems fine, my ethernet has a green tick next to it. When I tried to access my network, I got a message saying that it may be affected by a firewall.  As far as I know I have not installed any firewall, so is there one built in that I need to configure?

PLEASE HELP!:-(

---

### Post by Russty of Oz on 2006-08-26
just bring this back up the list.

---

### Post by CREEPING DEATH on 2006-08-27
All I can suggest is make sure DHCP is turned on, my cousin's Edubuntu box somehow thought it had a static IP and wouldn't connect once.

CD

---

### Post by Russty of Oz on 2006-08-27
Well I decided I had had enough of the problems on Kubuntu and have since reinstalled Ubuntu and now all my problems are gone.  Pity really, I do like Kubuntu but will wait till the KDE has improved a bit more.  Gnome seems a bit plain but it works, and that is the main thing.  

Russty.

---

### Post by MaximB on 2006-08-27
did you configure your connection ?
if not try in the terminal/console :
sudo pppoeconf

---

### Post by derred on 2006-08-27
If you like the way KDE looks, or are more comfortable in it, or wish to have it as your Desktop Enviroment, you can install it in Ubuntu. For example: 

I wanted to have KTTSD and KSayIt installed, and to be able to run them from their native desktop. I was now faced with three options.

1. install the KDE package (~200MB[-( )
Description: the K Desktop Environment official modules
 KDE (the K Desktop Environment) is a powerful Open Source graphical
desktop environment for Unix workstations. It combines ease of use,
contemporary functionality, and outstanding graphical design with the
technological superiority of the Unix operating system.
 This metapackage includes all the official modules that are released with
KDE. In addition to the core KDE modules, this includes multimedia,
networking, personal information manager (PIM), graphics, education, games,
web development, system administration tools, and other artwork and
utilities. This package does not depend on development packages.

2. install the kubuntu-desktop package (~100MB:-? )
Description: Kubuntu desktop system
 It's basicaly the core pack+ other things you find in kubuntu.

3. install the kde-core package (~50MB:D )
Description: the K Desktop Environment core modules
 KDE (the K Desktop Environment) is a powerful Open Source graphical
desktop environment for Unix workstations. It combines ease of use,
contemporary functionality, and outstanding graphical design with the
technological superiority of the Unix operating system.
 This metapackage includes the core official modules released with KDE. This includes just the basic desktop (browser, file manager, text editor, control center, panel, etc.) and important libraries and data, in addition to the aRts soundserver.

In the end I settled for "sudo apt-get install kde-core" to avoid any application removal dependencies, and I suggest you do the same. After the installation was complete you can install any other programs that you need. The thing is, you'll be installing them from KDE:D

---

### Post by Russty of Oz on 2006-08-27
Thanks that could be useful for programs like kdetv as I can't seem to get mythtv to work. 

Russty.:)

---

### Post by MaximB on 2006-08-27
or if you want just the interface - the windows "start" you can just install Kicker.
and you will still have your gnome menus.
try it.

in the terminal type :

sudo apt-get -f -y install gnome-panel kicker
gnome-panel & kicker &

---

### Post by Russty of Oz on 2006-08-27
**WOW!  FANTASTIC!** :grin: 

I never thought you could have both gnome AND KDE working together like this.  The BEST OF BOTH!  **COOL!**:cool: 

I am so excited! This is GREAT!

THANK YOU! THANK YOU! THANK YOU! DERRED & MAXDDARK

Russty.

---

### Post by Russty of Oz on 2006-08-28
Just one more question.  Now that I can have the KDE panel on Ubuntu, is there any way of keeping it there when I reboot, or do I have to type in 'gnone-panel & kicker &' every time?

Russty. :)

---


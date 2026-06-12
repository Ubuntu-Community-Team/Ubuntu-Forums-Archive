---
title: "Ubuntu 7.04 Server"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Peter Alien on 2007-10-02
Hello,

today i read a tutorial about creating a network with Ubuntu 7.04, but i got very confused about that. :)

One of the confusions is about the Server Operating System.

I have Ubuntu 7.04, so can anyone tell me if i can put it as a server in a Server Machine that exists in a Network? Or there is a server version of Ubuntu 7.04?

I'm asking this because that tutorial that i read has screenshots of Ubuntu instalation menu and it's different than mine!!!

If there is an Ubuntu 7.04 Server from where can i download it? Is it free?


By the way... does anyone know about some tutorial that can teach to mount a small intranet with Ubuntu 7.04? That could teach to configure Ubuntu to recognize PC Clients and a Router?


Many many thanks

---

### Post by dca on 2007-10-02
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) 
 
then put a check mark in 7.04 Server Edition
 
The only difference is one installs w/ a DE (GUI) Gnome which would be the Desktop Edition, the Server Edition is CLI only (No GUI)...  The only other difference is the server edition allows you to install, create, deploy a LAMP server off the cuff where as the desktop edition would require you to install the additional necessary packages.  Don't get confused w/ Windows XP versus Windows Server 2003.  Linux distributions don't work like that...

---

### Post by dca on 2007-10-02
...on second thought you may want to continue using the GUI-based desktop edition for now until you get used to Linux...  On top off all that great docs avail on Ubuntu's website, this one also helped:
 
[http://www.howtoforge.net/taxonomy_menu/1/1/50](http://www.howtoforge.net/taxonomy_menu/1/1/50)

---

### Post by Peter Alien on 2007-10-02
I still prefer Ubuntu with GUI... i don't have many experience with Linux :(

but tell me with GUI (Gnome) the Linux Server won't stay to much slow, right? :)

---

### Post by dca on 2007-10-02
You could always install the non-GUI server based version and from CLI:
 
sudo apt-get install ubuntu-desktop
 
...and that will install the entire Gnome DE....  I guess it's kinda' six in one hand, half dozen in the other...

---

### Post by az on 2007-10-02
> **Peter Alien said:**
> I still prefer Ubuntu with GUI... i don't have many experience with Linux :(

but tell me with GUI (Gnome) the Linux Server won't stay to much slow, right? :)

You can install the LAMP server packages from any Ubuntu system, include one with a desktop.  Not, it won't slow it down (unless you really need every single percentage of performace), although you will be going against best security practices - it is safer to have the least amount of installed software on a production server.

See:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

and
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by Peter Alien on 2007-10-05
Many many thanks ... i will do that :)

---

### Post by hasafraker on 2007-10-05
> **dca said:**
> You could always install the non-GUI server based version and from CLI:
 
sudo apt-get install ubuntu-desktop
 
...and that will install the entire Gnome DE....  I guess it's kinda' six in one hand, half dozen in the other...

...sudo apt-get install ubuntu-desktop

you sir are my hero, I've messed with ubuntu a few times but my RH9 server just died after 8yrs and 3 cpu's 4 mobo's it finally went down for the count and a friend of mine recommended to try it. I have a Debian box at work that I tinker with but nothing serious, I do prefer the gui. Thanks for the info.

H.

---


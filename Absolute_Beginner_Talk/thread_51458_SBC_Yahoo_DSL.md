---
title: "SBC Yahoo DSL"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by USAOwnz on 2005-07-24
I can't connect to the interenet, or can't figure out how to connect to the internet via my DSL modem(5100) on Ubuntu. Anybody have the same modem and connection and willing to help me out?

---

### Post by aysiu on 2005-07-24
I don't have the same modem, but I do have SBC Yahoo! DSL and have had no problems. When you installed Ubuntu, what happened when the text-installer said it was going to try to set up DHCP? Did everything seem to go well?

---

### Post by USAOwnz on 2005-07-24
[QUOTE=aysiu]I don't have the same modem, but I do have SBC Yahoo! DSL and have had no problems. When you installed Ubuntu, what happened when the text-installer said it was going to try to set up DHCP? Did everything seem to go well?[/QUOTE]It didn't go well, I skiped it for that reason...

---

### Post by aysiu on 2005-07-24
What was the exact error?

---

### Post by USAOwnz on 2005-07-24
[QUOTE=aysiu]What was the exact error?[/QUOTE]
I don't know, I skipped it. It said that something about it could detect somethign and that maybe it could be that my ISP or something does not use DHCP

---

### Post by aysiu on 2005-07-24
Try this. Reinstall Ubuntu and this time don't skip DHCP. Let us know if you still can't connect to the internet.

[http://www.dhcp.org/](http://www.dhcp.org/)

---

### Post by USAOwnz on 2005-07-24
[QUOTE=aysiu]Try this. Reinstall Ubuntu and this time don't skip DHCP. Let us know if you still can't connect to the internet.

[http://www.dhcp.org/](http://www.dhcp.org/)[/QUOTE]Eh, fixed it running pppoeconf on the terminal.

---

### Post by USAOwnz on 2005-07-24
How do you navigate to a specific folder on the terminal?

---

### Post by Knome_fan on 2005-07-24
cd

for example:
cd /home/ralph/stuff will take me to my stuff folder no matter where I am, but if I'm allready in /home/ralph (which is the default when opening a terminal) cd stuff is enough.

And make sure to use the tab key a lot, it will autocomplete the path for you.

---

### Post by USAOwnz on 2005-07-24
Ok.
This might be a bit off, but do you know where I might be able to find a K-lite codec packet for Ubuntu?

---

### Post by Knome_fan on 2005-07-24
You probably want w32codecs.

To get them you'll first have to add the backports-extra repository to your soures.list.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Now you can simply use synaptic to install w32codecs.

If you want to use them with totem (the default media player for Ubuntu) you'll also have to make sure to install totem-xine (this will replace totem-gstreamer automatically which isn't able to use these codecs). 

Then you should be ready to go.

---

### Post by USAOwnz on 2005-07-24
[QUOTE=Knome_fan]You probably want w32codecs.

To get them you'll first have to add the backports-extra repository to your soures.list.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Now you can simply use synaptic to install w32codecs.

If you want to use them with totem (the default media player for Ubuntu) you'll also have to make sure to install totem-xine (this will replace totem-gstreamer automatically which isn't able to use these codecs). 

Then you should be ready to go.[/QUOTE]
Thanks!

---

### Post by USAOwnz on 2005-07-24
Still can't seem to play certain video files....

---

### Post by codejunkie on 2005-07-24
[QUOTE=USAOwnz]Still can't seem to play certain video files....[/QUOTE]
if your using totem that comes with ubuntu that's why you cant play most video files it wont play protected formats install totem-xine and gstreamer-plugins and libdvdcss2 if your trying to watch dvd's w32codecs and that should play about  everything.

---

### Post by USAOwnz on 2005-07-24
Shoudl it work with VLC? Because I just installed it and it still doens't work. All I get is audio. Furthermore, I can seem to play mp3s.

---

### Post by codejunkie on 2005-07-24
[QUOTE=USAOwnz]Shoudl it work with VLC? Because I just installed it and it still doens't work. All I get is audio. Furthermore, I can seem to play mp3s.[/QUOTE]
i dont know about vlc i think i had to change some video output settings and add some more codecs to get it to work i cant exactly rembember how though but i think i had to set it to use xv as the video output but im not sure that will work.
edit: the reason your not able to play mp3's is you need to install the  
gstreamer-plugins packages.

---

### Post by USAOwnz on 2005-07-24
How the heck do you install them?

---

### Post by codejunkie on 2005-07-24
[QUOTE=USAOwnz]How the heck do you install them?[/QUOTE]
click on the System menu the under Administration then go to Synaptic package manager when you open synaptic click search enter the name of the package you want hit search when you find the package right click on it choose mark for installation when your done choosing software hit apply and it will download and install them for you.
but if you havent already you need to add some repositories to /etc/apt/sources.list file follow this guide to add extra repositories
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
and then try installing the software hope this helps.

---

### Post by USAOwnz on 2005-07-24
Thanks, bud.

---

### Post by USAOwnz on 2005-07-25
Ok, how can I install Virtual Machine in order to run Limewire. Also, I don't get how to install Azureus, it's not an RPM, soo... I have difficulties on that one.

---

### Post by codejunkie on 2005-07-25
[QUOTE=USAOwnz]Ok, how can I install Virtual Machine in order to run Limewire. Also, I don't get how to install Azureus, it's not an RPM, soo... I have difficulties on that one.[/QUOTE]
you dont have to install an virtuial machine to install lime wire they make a linux version that runs the same as the windows version just download the .rpm package of lime wire and install it like this ```
sudo alien -d nameoffile.rpm
``` this will make a .deb package of limewire now install the .deb file like this 
```
sudo dpkg -i nameoffile.deb
``` and azureus 
open synaptic click search type azureus and install. or you can download the linux GTK version from [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/) place it in your home folder rightclick on it choose extract enter the folder double click the azureus.sh file and click run.

---


---
title: "flash player 7"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-27
i have just been to a website and i need flash player 7
can someone please point me to info on installing flash 7
i cant find it in the synaptic packet manager.(why is this)
also if you could point me to some info on how unix installs programs differently that too would be apretiated.
im guessing its different coz when i google it i get pages of code mostly and im just learning.
not used to not having .exe's
i have searched the threads before you say anything...
hence i dont like the idea of installing wine.

---

### Post by ashokpappu on 2006-09-27
flash runs natively on linux 

[http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)

download this and follow instructions

---

### Post by Tamil on 2006-09-27
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by ThrobbingBrain66 on 2006-09-27
flash is in the repos...youll have to enable the universe and multiverse repos, but the name you want to search for is flashplugin-nonfree

---

### Post by uk_sphinx on 2006-09-27
thank you

---

### Post by uk_sphinx on 2006-09-27
i followed the link you gave me.
when i downloaded the file it appeared on my desktop.
the instructions told me that when i extract it, it should produce a folder in \
in the extration utility it was set by default to extract to desktop.when i changed it to root (\) it said i dont have the right to do that. is this because i still have the default oem account? 
is it refering to the tape drive privilage?
what the hell is a tape drive anyways?

i extracted the file to desktop and clicked on it with my mouse instead of using the command terminal.
i dont think that worked as the terminal poped up briefly and then disapeared.

---

### Post by uk_sphinx on 2006-09-27
back to the top we go
someone help please

---

### Post by 3rdalbum on 2006-09-27
Open up a terminal (Applications > Accessories > Terminal).

Now type the following:

```

sudo su #then type your password when it asks
cd Desktop
./flashplayer-installer

```

An explanation of these lines:

**sudo su** tells Ubuntu that you want to switch to the root account, as you need to be root in order to install software.
**cd Desktop** changes the current working directory to the Desktop.
**./flashplayer-installer** runs the "flashplayer-installer" program, inside the current working directory.

I suggest you go to [www.linuxcommand.org](www.linuxcommand.org) and read their tutorials on the command-line. Some installers, like the Flash Player installer, require you to run the program at a command-line.

---


---
title: "Installing Programs on Ubuntu [Resolved]"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2007-02-16
Hello, I have been using Ubuntu for almost a year know and I still can't get program to install when I download them of the internet.  Can some please help me on this.  I am not to good with Terminal mode.  Please Help.

---

### Post by Sklasko on 2007-02-16
Installing programs from source tarballs is not recommended for beginners. I still avoid it as much as possible. I recommend searching for the program your looking for in the repos or trying to find a .deb for it.

---

### Post by Cardmaster91 on 2007-02-16
Programs are different, sometimes it will be as easy as downloading and click open. Some Are already available in synaptic, and some can be created through compilng source codes. I don't know all that much about linux either, but alot of things i download have instructions right on the website. Or if it is a .deb, you could simply double click on it. Some packages are already available in the synaptic, and yould download them right there. A good idea would be to ask how to install a specific program.

---

### Post by NeoGreen on 2007-02-17
I looked under synaptic and didn't find a driver for Adobe Flash.  I was able to download it to the desktop but no luck installing.

---

### Post by NeoGreen on 2007-02-17
this file is a tar. gz file.

---

### Post by rosieg on 2007-02-17
Hi there,

I never install software unless I can get it through Synaptic or the Add/Remove programs function. I have tried in the past and tend to lose it, or can't get it to work.

With regards to installing Flash, I just did it through Applications -> Add/Remove programs and searched for Flash. Works fine.

---

### Post by NeoGreen on 2007-02-17
Awesome, I will try it.:) :)

---

### Post by mskobier on 2007-02-17
Nono,
      Do a web search for a program called Automatix. Navigate to the link for your particular Ububtu distro and click. When the window opens, click install and sit back. I will ask for authorization to install. Once it is installed, it will be added to the application menu under system tools. click on it and follow the instructions. It automates a some of the commonly used add in programs such as Acrobat and Flash Player. The download is free(donation requested) and it is self configuring.

Mitch

---

### Post by xpod on 2007-02-17
This place might help with the many installation methods

[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

---

### Post by NeoGreen on 2007-02-17
It worked thanks for the information.  :)

---

### Post by linux_kid on 2007-02-17
If you still want instructions for Adobe Flash, download the .tar file from adobe
Click on the .tar file and extract it
In terminal, type
```
cd ~/Desktop/install_flash_player_9_linux
```

then type in the same terminal, 
```
sudo ./flashplayer-installer
```
and keep press enter twice to install it in firefox.

If you need any more help, post in this thread. :popcorn:

---

### Post by NeoGreen on 2007-02-17
Thanks for the help, I really appreciate your help.:)

---

### Post by NeoGreen on 2007-02-17
Linux_Kid, I tried in your way to see if it would work and I keep getting this error:

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): 

How do I find the path?

---

### Post by linux_kid on 2007-02-17
I'm in windows right now, but the path should be similar to
/home/{username}/.mozilla
where username is your username, without the brackets

---

### Post by NeoGreen on 2007-02-19
Thanks for the info.

---


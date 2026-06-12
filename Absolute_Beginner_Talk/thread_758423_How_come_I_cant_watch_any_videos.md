---
title: "How come I cant watch any videos?"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Stephen4785 on 2008-04-18
I just installed Ubuntu so Im a complete newb. I tried to follow these instructions [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
I did what it said to do and when I enter this in the terminal (sudo apt-get install ubuntu-restricted-extras) I will eventually get a dialog box that says I have to agree to these terms and conditions and at the bottom says <ok> . I tried hiting enter like the other boxes that popped up but nothing happens. I had to close the terminal and Im not sure if I should try it again or not. Im trying to be able to watch videos on myspace/youtube/college humor/etc... and have yet to succeed.
I read the articles for beginers and Im still not sure what the hell Im doing so please explain it so I might comprehend what the heck is going on.
Thanks
   Stephen

---

### Post by Pasty-Flawss on 2008-04-18
have you downloaded adobe flash player?

---

### Post by Crafty Kisses on 2008-04-18
Are you using Firefox or Opera?

---

### Post by NightwishFan on 2008-04-18
For youtube:
```
sudo apt-get install flashplugin-nonfree
```
For others:
```
sudo apt-get install vlc
```
If you want to use your own player generally try to open in totem and it will ask for codecs, and install the ones you need. Otherwise try the ubuntu-restricted-extras again. If you get any error messages with the commands I gave you it will be easy to fix. (vlc player owns though =D)

---

### Post by bumanie on 2008-04-18
Firstly open terminal Applications --> Accessories --> terminal and copy and paste this into terminal (assuming you are using gutsy gibbon)

> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
hit enter. Then

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O - | sudo apt-key add - && sudo apt-get update
This will add medibuntu to your /etc/apt/sources.list and enable the authentication key.
Then follow this guide [http://ubuntuguide.org/wiki/Ubuntu:G...ack_Capability](http://ubuntuguide.org/wiki/Ubuntu:G...ack_Capability) Then follow this to enable mozilla plugins
[http://ubuntuguide.org/wiki/Ubuntu:G...owser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:G...owser_Plug-ins)
I personally use gnash and find it fine, that's not everyone's experience however. I would advise installing vlc player as it plays almost every codec there is.
Hope this works for you.

---

### Post by Stephen4785 on 2008-04-18
I downloaded adobe to my desktop but cant figure out how to install it. Im using fire fox. I get all the way to this message box that pops up "Configuring sun-java6-jre" and then cant get it to do anything. I tried re-opening the terminal and starting over and it said I had to do this and that to fix the problem so I followed the instruction(even figured out I needed to type sudo before everything:) ) and got right back to the same dialog box that says <ok> at the bottom.

---

### Post by NightwishFan on 2008-04-18
Did you try the command I gave you to install flash?

---

### Post by Stephen4785 on 2008-04-18
> **NightwishFan said:**
> Did you try the command I gave you to install flash?

The second one went fine but when I did the first command it says "Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed."
?

---

### Post by NightwishFan on 2008-04-18
This happened to me before. I think it is an error with the repository. Perhaps install the package with synaptic. Also try again the command later if synaptic does not work for same reason.

---

### Post by Stephen4785 on 2008-04-18
Well I got the adobe plug in to work and I can watch videos now :KS. But I get no sound?

---


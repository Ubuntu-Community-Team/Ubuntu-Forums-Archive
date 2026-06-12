---
title: "flash"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by mattroy89 on 2008-01-27
Having trouble installing flash. Could someone please help.

---

### Post by ryanVickers on 2008-01-27
Flash Player, or actually Flash?
for Flash, since there isn't a Linux version yet, you will have to run it in Wine or a VM, but the flash player with 32 bit should be as simple as just going to a page that needs it, and installing plugins.  Gutsy makes it that simple for every architecture though ;)

---

### Post by seventhc on 2008-01-27
go here
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
download the first file, then scroll down a little. Very clear instructions there. it's easy. :)

---

### Post by mattroy89 on 2008-01-27
For some reason that doesn't work, is there an easier way? I am new to this.

---

### Post by seventhc on 2008-01-27
That should work, can you tell me what you did when you tried the install, and what errors you got in return?

---

### Post by Tristicus on 2008-01-27
In Firefox, if you view a YouTube video for example, you can click the get Flash or w/e and it should ask you to install one....

---

### Post by mattroy89 on 2008-01-28
I went to youtube, This is where I first tried to install it. Everything installs ok but then the usage agreement  comes up and I can't press ok. Any help? And thanks so far.

---

### Post by seventhc on 2008-01-28
> **mattroy89 said:**
> For some reason that doesn't work, is there an easier way? I am new to this.
I don't understand, how is that not easy>>??? it's like 3 steps
download, (just open it with archive manager) [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
Then in your terminal
navigate to directory 
if on your desktop
```
cd /home/your_username/Desktop/install_flash_player_9_linux

```if in your home folder
```
cd install_flash_player_9_linux
```then
```
./flashplayer-installer
```

---

### Post by seventhc on 2008-01-28
I'm happy to help you, but just please tell me what part you don't understand here and I will be happy to explain it. (step by step if necessary)
For instance, when you click on the download link, don't choose save to disk, choose 'open with' and then a box will open with a folder in it, highlight the folder then click on the button "Extract" from there you can choose the location. choose either your desktop or the home folder.
Then go the menu for programs. "Applications>Accessories>Terminal
and that is where you enter the commands from above.
just paste them in but change your_username to the name you use when you login to the computer.

---


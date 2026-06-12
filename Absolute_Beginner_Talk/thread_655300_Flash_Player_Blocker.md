---
title: "Flash Player Blocker?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by packrat on 2008-01-01
I'm stumped...

Have Adobe Flash Player installed the nonfree v...and, get the following message:

This CNN.com feature is optimized for Adobe Flash Player version 8 or higher.
You are currently using Flash Player 0
Get Flash Player

Removed it and installed gnash...here's the message -
This CNN.com feature is optimized for Adobe Flash Player version 8 or higher.

You are currently using Flash Player 0
Get Flash Player

What's up? Thanks.

---

### Post by Jonne on 2008-01-01
seems to work fine for me. Maybe you have noscript or adblock blocking some javascript?

---

### Post by hyper_ch on 2008-01-01
the installation of flash is currently bugged and you'll need to get the tar.gz file from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Follow the insturctions on the site and use not
```

./flashplayer-installer

```
but
```

sudo ./flashplayer-installer

```

---

### Post by packrat on 2008-01-01
OK. So, where do I start to look to resolve the maybes you propose? Thanks.

---

### Post by packrat on 2008-01-01
> **hyper_ch said:**
> the installation of flash is currently bugged and you'll need to get the tar.gz file from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Follow the insturctions on the site and use not
```

./flashplayer-installer

```
but
```

sudo ./flashplayer-installer

```

OK. Got it downloaded on my desktop. Now, what?

---

### Post by hyper_ch on 2008-01-01
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
> 
.tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.


---

### Post by packrat on 2008-01-01
Thanks. I suppose where I stump my toe is on Number 4...4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer.

How do I navigate to the the "install_flash_player_9_linux" in terminal...I'm almost illiterate in these matters???

---

### Post by PmDematagoda on 2008-01-01
You can use the following command:-
```
cd install_flash_player_9_linux
```

I highly recommend that you read this very useful [page]("https://help.ubuntu.com/community/UsingTheTerminal") on the basic ways of using the terminal.

---

### Post by packrat on 2008-01-01
sam@sam-desktop:~$ cd install_flash_player_9_linux
bash: cd: install_flash_player_9_linux: No such file or directory
sam@sam-desktop:~$


OK...what next?

---

### Post by Taboo Mirage on 2008-01-01
Just type these commands, one after the other, into a terminal:

```
cd ~
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -zxf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins/
```
It'll then work.

---

### Post by kerry_s on 2008-01-01
try in terminal:
mv ~/.mozilla/firefox/pluginreg.dat  ~/.mozilla/firefox/pluginreg.dat.old

restart firefox

---

### Post by packrat on 2008-01-01
> **Taboo Mirage said:**
> Just type these commands, one after the other, into a terminal:

```
cd ~
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -zxf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins/
```
It'll then work.

Want to thank you, and everyone else...ran the last and it appears to have installed but still flash player does not work. May re-install 7.10 or try 6.06?

---

### Post by Jonne on 2008-01-01
what firefox extensions do you have? And are you certain you haven't disabled javascript in the preferences?

Also, do other sites work? (youtube, etc)

---

### Post by packrat on 2008-01-02
Thanks. Tried it all. Even reinstalled and tried all the help, again...guess I'll wait for the next update...disappointed in Gutsy...:looks like Hardy Heron 8.04 LTS during April 2008...only 4 months...[http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29](http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29)

---


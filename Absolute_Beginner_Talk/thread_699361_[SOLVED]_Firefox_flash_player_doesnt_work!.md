---
title: "[SOLVED] Firefox flash player doesnt work!"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Meox on 2008-02-17
Hello, 
        I have been having a bit of a problem with the Firefox Flash player.. you see it wont load anything at all at youtube it just gives me a loading screen and it doesnt load and on other websites it just shows a blank screen.. whats wierd though is that it was working great yesterday... but now it wont work.. any suggestions?

---

### Post by jan quark on 2008-02-17
try this in terminal
```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by lncoll on 2008-02-17
Hi:
I know there are easyer ways to do but this the one I use.
Download from adobe.com the linux flash player.
Uncompress it in a folder, close all firefox instances, Execute the installer as root or with sudo, this way it works for every user.
Start firefox and voila!! it works (we hope)  ;)

---

### Post by Meox on 2008-02-17
ok i have ran the code im my terminal it has removed non-free flash player.. what do i do now?

---

### Post by Meox on 2008-02-17
oh wait it has re-installed flash player plugin.. i'll go check to see if it works

---

### Post by Meox on 2008-02-17
OK... i have installed the Flash player from my terminal.. now i go onto youtube and i get nothing i just get a loading screen that doesnt load at all.What should i do now?

---

### Post by Meox on 2008-02-17
This has gotten extremely frustrating! please anyone can you help me with my flash player plugin for Firefox.

---

### Post by mbailey90 on 2008-02-17
go to adobe.com and dowload the .tar.gz files for the flash player

---

### Post by jan quark on 2008-02-17
and use this small guide to see how to install flash from the adobe site

[http://laiconic.quotaless.com/tutorial3.html](http://laiconic.quotaless.com/tutorial3.html)

---

### Post by seventhc on 2008-02-17
Go to
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
and download the first file
or just download this
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
It's from their site then[LIST=1]
[*]Unpackage the file. A directory called install_flash_player_9_linux will be created.
[*]In terminal, navigate to this directory and type *./flashplayer-installer*                   to run the installer. Click Enter. The installer will instruct                   you to shut down your browser(s).
[*]Once the installation is complete, the plug-in will be installed in your Mozilla browser.[/LIST]

---

### Post by Meox on 2008-02-17
ok heres what you should know ok.. i have downloaded the .tar.gz flash player files i have installed them and it still will not work

---

### Post by seventhc on 2008-02-17
I've never known this way to fail before, how exactly did you install it?
Also have you tried looking at a different vid on youtube? Maybe it's the vid that is failing.
If you type 
```
[I]about:plugins

```[/I] in the address bar what shows up?

---

### Post by Meox on 2008-02-17
I thank you all soo much.. apparently i needed to reinstall via synaptic package manager.. i thought it might work and it did thanks to you all.. sorry if i may have wated your time i was just in a tight spot.. well i shall keep in mind if my flash player ever messes up again..

---


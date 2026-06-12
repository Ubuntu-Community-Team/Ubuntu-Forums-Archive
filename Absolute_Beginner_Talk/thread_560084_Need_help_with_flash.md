---
title: "Need help with flash"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by krumble on 2007-09-25
Ok well I have been trying to install flash on my laptop that I just got.  I went to a wiki site on how to install it and I followed the instructions and tried to install the flash-nonfree and it worked, but nothing was working still.  I continued to read and it said that if it didnt work that I should try the gnash.  After I installed the gnash everytime I try to go to youtube or any site that has any sort of flash on it like a slide show on myspace my computer will crash and restart or if I can get to it in time the flash video or what ever will be all wierd.

Any help would be appreciated.  Also if I cant solve this is there any way to uninstall gnash because I would rather have the missing plugin thing instead of having my computer crash every time.

THanks in advanced.

---

### Post by Dr Small on 2007-09-25
How did you install gnash ?
If you installed it from the repositories in the command line, then type:
```
sudo apt-get remove gnash
```

Dr Small

---

### Post by krumble on 2007-09-25
Thank you.  Now I dont crash when ever I go to youtube or myspace.  

Does anyone know how to install flash now? I dled the linux version from the site and when I go to install it it says select the location to be installed (ie: /usr/lib/mozilla)  but when I type it in it says that I typed in an incorrect directlory.  So I was wondering how the command line goes so that I can install it. 


And can anyone link me to a guide on playing videos such as wma or what ever in mozilla?


THanks again.

---

### Post by unisol on 2007-09-25
in synaptic package manager do a search for flash nonfree. it should be there thats how i installed mine using gutsy

---

### Post by alienexplorers on 2007-09-25
Down load the tar.gz version of flash player at this site:
> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
> .tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.



---

### Post by krumble on 2007-09-25
I tried the add/remove program thing, but that doesnt work.  It says that I need to get the latest version of flash when ever I go to youtube.  


When I try to install flash from the site I get as far as to pick where to install it.  I know i have to install it in "...../usr/lib/mozilla-firefox"   but I dont know what I should put for the "......"

---

### Post by Gremlinzzz on 2007-09-25
get Option 1: .tar.gz 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
right click on package choose extract here infolder you will see flashplayer installer click it choose run in terminal follow directions and your done:guitar:

---

### Post by krumble on 2007-09-25
I know that, but when I go to install it I get stuck at where it says to install.


[IMG]http://i137.photobucket.com/albums/q210/DJ_KRUMBLE/Screenshot-12.png[/IMG]


It says that I need to select the directory that firefox is in.  I know it is in the ....../usr/lib/mozilla-firefox, but I dont know what the ...... part should be.

---

### Post by Gremlinzzz on 2007-09-26
open the flashplayer folder right click on libflashplayer.so choose copy. then go too home dir click view then click show hidden files find folder mozilla in that folder is plugins folder open right click and choose paste.thats it:guitar:

---

### Post by erfahren on 2007-09-26
/usr/lib/firefox/plugins

Flash doesn't really even need to be installed that way, you just basically need to copy the files for Flash into a directory and then create symlinks to them in the Ffx/plugins directory.

try this:

extract the Flash archive and change directories into it, then;
```

sudo mkdir /usr/lib/flashplugin-nonfree-9

```
```

sudo cp ./flashplayer.xpt /usr/lib/flashplugin-nonfree-9

```
```

sudo cp ./libflashplayer.so /usr/lib/flashplugin-nonfree-9

```
```

sudo ln -s /usr/lib/flashplugin-nonfree-9/flashplayer.xpt /usr/lib/firefox/plugins

```
```

sudo ln -s /usr/lib/flashplugin-nonfree-9/libflashplayer.so /usr/lib/firefox/plugins

```

---

### Post by djchandler on 2007-09-26
No matter what, eventually you're going to need more then these. Go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and you can get linked to all the codecs and unsupported commercial software (by Ubuntu) that works well in Ubuntu, as purported by medibuntu's website. You can directly download the .deb files. Then all you have to do is double-click on the downloaded files to install them and follow the instructions. Very simple, very easy.

---

### Post by krumble on 2007-09-26
Umm I'm not sure which 1 I use, the i386, amd64, or powerpc

---

### Post by weedeatr on 2007-09-26
> **krumble said:**
> I know that, but when I go to install it I get stuck at where it says to install.


[IMG]http://i137.photobucket.com/albums/q210/DJ_KRUMBLE/Screenshot-12.png[/IMG]


It says that I need to select the directory that firefox is in.  I know it is in the ....../usr/lib/mozilla-firefox, but I dont know what the ...... part should be.

go into the flash folder and click on install it will ask terminal run or view i think click terminal and follow prompts

---


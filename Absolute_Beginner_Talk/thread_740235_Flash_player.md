---
title: "Flash player"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by doomedfire on 2008-03-30
I wanna be able to watch youtube veoh etc. Can someone please walk me threw the steps, i am currently using Ubuntu 7.10

Thx in advance.

---

### Post by freetonik on 2008-03-30
If you go to youtube in your Firefox, it will tell you that you have no neccesery plugin and ask if you want to install it. Just say YES and click couple buttons - there you'll have flash

---

### Post by abhiroopb on 2008-03-30
try this in the terminal (applications>accessories>terminal)

sudo apt-get install flashplugin-nonfree

this should install flash which allows you to watch youtube videos.

Let me know if this helps

(more info: on EVERYTHING Ubuntu: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy))

---

### Post by doomedfire on 2008-03-30
Says to install it even though i just did then when i go to install it it says its the newest version

---

### Post by abhiroopb on 2008-03-30
so when you type it in it says already newest version? And when you try playing a video what does it say? Try restarting firefox (or whatever browser you are using).

---

### Post by doomedfire on 2008-03-30
"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player." Doesnt even get to play a movie that is just there. so i click to get the latest version and it says package "flashplugin-nonfree" already installed.

I just want to watch anime :'(

---

### Post by collinp on 2008-03-30
Go to edit - preferences and make sure the box next to "Enable JavaScript" is checked.

---

### Post by abhiroopb on 2008-03-30
Restart the computer (this usually helps with a lot of problems :P) If it still doesn't work:

```

sudo apt-get remove flashplugin-nonfree --purge

```

then do:

```

sudo apt-get install flashplugin-nonfree

```

Then restart your browser and see if that helps.

If this doesn't work let us know.

---

### Post by doomedfire on 2008-03-30
It's enabled. What else could it be?

---

### Post by collinp on 2008-03-30
Follow what the person after my post said.

---

### Post by doomedfire on 2008-03-30
"Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
"

 What does that mean? it happened after i typed 
"sudo apt-get install flashplugin-nonfree"

---

### Post by abhiroopb on 2008-03-30
Could I have your computer specs please

---

### Post by lswest on 2008-03-30
download [this file]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux") and extract it (right-click and choose "extract here") then run it by doing this: right-click it and under the properties tab make sure "allow executing as a file" or similar is checked, and then double-click it.  Follow the instructions to install.  And if it asks, firefox is installed in /usr/lib/firefox/

Or, for system-wide install:
```
cd [location of the file]
sudo sh flashplayer-installer
```

---

### Post by doomedfire on 2008-03-30
How would i find them?

---

### Post by lswest on 2008-03-30
the computer specs are unnecessary, the flashplayer md5sum mismatch was a problem, could have sworn it was fixed a while ago, but it doesn't matter, the fix i posted above should work.

---

### Post by abhiroopb on 2008-03-30
Its fine: I've found the OFFICIAL fix:

you can read about it in more detail here: 
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

but the main thing:

From the menu:
System -> Administration -> Software sources -> be sure than you have selected the "main", "universe", "restricted" and multiverse".
Then go to the Updates tab -> check "security", "updates" and "proposed"
Now "Close" and "Reload".

after that, do this in the terminal:
sudo apt-get install flashplugin-nonfree

See if this works.

If not I've found another fix (but read the thread if you are getting a specific error as someone may have gotten it as well).

---

### Post by doomedfire on 2008-03-30
"17:23:43 (159.74 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
Flash Plugin installed.
" 

Went on youtube and veoh, video played Ty so much guys. :) :) :)

---

### Post by bratliff on 2008-04-04
I have video no sound.
Ratliff

---


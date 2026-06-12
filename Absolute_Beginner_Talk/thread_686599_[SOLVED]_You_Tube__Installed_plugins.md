---
title: "[SOLVED] You Tube / Installed plugins"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by nomojoe on 2008-02-03
Hi,

I have just installed ubuntu, when i was running it as a live cd i could install the flash plugins and  watch you tube videos. 

Now I have installed ubuntu, i try you tube and it says install missing plugins which I then do, only i still cant watch them.  It says install missing plug ins. I click on here and it says already installed????

Help anyone??

---

### Post by jaytek13 on 2008-02-03
There is a known bug currently with installing the package from the repos. There are some "fixes" but I personally just install the plugin manually.

First uninstall the plugin

```

sudo apt-get remove flashplugin-nonfree
```

Go here ( [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux) ) and download the tar.gz package and save it to your desktop

Open a terminal and go to your Desktop directory
```
cd /home/your_username/Desktop
```

Extract the file that you downloaded
```
tar -zxvf install_flash_player_9_linux.tar.gz
```

go into the directory you just extracted
```
cd install_flash_player_9_linux
```

Run the installer
```
sudo ./flashplayer-installer
```


And then restart your browser and flash should be working.

---

### Post by nomojoe on 2008-02-03
Thank you very much for that.

All working.:)

---

### Post by mcy782 on 2008-02-05
Thanks. I tried your advice for a manual install and it worked like a charm!

---


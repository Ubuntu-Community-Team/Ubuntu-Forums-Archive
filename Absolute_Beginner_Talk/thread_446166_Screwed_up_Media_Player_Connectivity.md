---
title: "Screwed up Media Player Connectivity"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by latanerp on 2007-05-16
I don't even remember why, exactly, I did it--but in my settings for Media Player Connectivity under Media Players for divx I changed the path to /usr/bin/X11/totem-xine (I think I was trying to get the file to open in Xine instead of Totem, I forget) ...after restarting Firefox, it made it so that not only does the following error appear when I click on a DivX file

> Unable to find the video player (check Tools menu, MediaPlayerConnectivity...)

Technical informations
/usr/bin/X11/totem-xine
[http://divx-129.vo.linwd.net/stage6vid/1223248.divx](http://divx-129.vo.linwd.net/stage6vid/1223248.divx)

%f
----------------
[Exception... "Component returned failure code: 0x80520006
(NS_ERROR_FILE_TARGET_DOES_NOT_EXIST) [nslLocalFile.isFile]" nsresult: "0x80520006
(NS_ERROR_FILE_TARGET_DOES_NOT_EXIST)" location: "JS frame ::
chrome://mediaplayerconnectivity/content/mpc-overlay.js :: mpc_executeApp :: line 873" data: no]

but now when I enter the configuration to change it, the option for DivX is just gone.  Does anyone know where I can access the config file to change the path back to  /usr/bin/X11/totem ???  

** I should also note that I already tried uninstalling and reinstalling, but it just kept the old configuration

Thanks in advance.

---

### Post by klytu on 2007-05-18
> **latanerp said:**
> I don't even remember why, exactly, I did it--but in my settings for Media Player Connectivity under Media Players for divx I changed the path to /usr/bin/X11/totem-xine (I think I was trying to get the file to open in Xine instead of Totem, I forget) ...after restarting Firefox, it made it so that not only does the following error appear when I click on a DivX file
> Unable to find the video player (check Tools menu, MediaPlayerConnectivity...)

Technical informations
/usr/bin/X11/totem-xine
[http://divx-129.vo.linwd.net/stage6vid/1223248.divx](http://divx-129.vo.linwd.net/stage6vid/1223248.divx)

%f
----------------
[Exception... "Component returned failure code: 0x80520006
(NS_ERROR_FILE_TARGET_DOES_NOT_EXIST) [nslLocalFile.isFile]" nsresult: "0x80520006
(NS_ERROR_FILE_TARGET_DOES_NOT_EXIST)" location: "JS frame ::
chrome://mediaplayerconnectivity/content/mpc-overlay.js :: mpc_executeApp :: line 873" data: no]


but now when I enter the configuration to change it, the option for DivX is just gone.  Does anyone know where I can access the config file to change the path back to  /usr/bin/X11/totem ???  

** I should also note that I already tried uninstalling and reinstalling, but it just kept the old configuration

Thanks in advance.

You should be able to change this in the firefox menu Tools>Media Player Connectivity>Configure.

EDIT: At first I missed that part where you tried this but couldn't find the option for DivX. The settings are stored in the file prefs.js found in your /home/<your user name>/.mozilla/firefox/<some encrypted name unique on your system>.default directory.  You can open the prefs.js file with a text editor, but be careful when changing it. [COLOR="RoyalBlue"]**In fact probably the safest way to make the changes is by typing about:config  in the Firefox address bar. Then you can use the filter to find mediaplayerconnectivity options or divx or whatever you want to change, right click the appropriate line and change what you want.**[/COLOR]

Also, I think you want to use /usr/bin/totem for totem or /usr/bin/xine for xine. You can check with  this command in a terminal window: ```
which totem
``` or ```
which xine
```

---

### Post by beuh_dave on 2007-05-19
I was having the same problem, thanks for the help! :)

---

### Post by latanerp on 2007-05-20
thanks very much, klytu, that was very helpful--changing it in about:config did the trick! :)

---


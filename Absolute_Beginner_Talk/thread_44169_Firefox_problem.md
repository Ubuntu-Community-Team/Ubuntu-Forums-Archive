---
title: "Firefox problem"
date: 2005-06-24
forum: Absolute Beginner Talk
---

### Post by someone447 on 2005-06-24
I am having trouble updating firefox, it says my version isnt high enough for the extensions.
I am also having trouble downloading and installing java and flash plugins.
Anyhelp would be greatly appreciated.

---

### Post by user on 2005-06-24
[QUOTE=someone447]I am having trouble updating firefox, it says my version isnt high enough for the extensions.
I am also having trouble downloading and installing java and flash plugins.
Anyhelp would be greatly appreciated.[/QUOTE]
 goto about:config from firefox and change the version number to 1.04

---

### Post by someone447 on 2005-06-24
it doesnt let me go to about:config it just says this
XML Parsing Error: syntax error
Location: jar:resource:///chrome/toolkit.jar!/content/global/config.xul
Line Number 1, Column 1:Mode != FIND_NORMAL) closeFindBar(); }, gQuickFindTimeoutLength);

---

### Post by Kvark on 2005-06-24
Changing general.useragent.vendorSub to 1.0.4 at about:config gave me access to the extensions site. But you get an error when going there... The values at about:config should correspond to some config file, so it should be possible to change them there too, but I can't figure out which one.

[This will get flash to work.](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

As for java, install sun's jre, it will work with firefox right away if you use synaptic or apt-get.

---

### Post by someone447 on 2005-06-25
i download flash from your link but when i try to extract it, it doesnt work
/bin/sh: tar: command not found

---

### Post by manicka on 2005-06-25
[QUOTE=someone447]it doesnt let me go to about:config [/QUOTE]

how are you trying to get to about:config?

---

### Post by someone447 on 2005-06-25
i got it now, I restarted and it worked.  I dont know why that happened, but thanks for all the help, i still cant get flash to install though.

---

### Post by Kvark on 2005-06-25
For flash:

1. [Download the archive.](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
2. Click on the archive to extract it.
3. Open a termial and navigate to the "install_flash_player_7_linux" directory you got when extracting.
4. Type "sudo ./flashplayer-installer"
5. Make sure firefox is not running.
6. When the installer asks where your browser is, enter "/usr/lib/mozilla-firefox"

---

### Post by manicka on 2005-06-25
Flash player 7  is also available the easy way through apt or synaptic

---


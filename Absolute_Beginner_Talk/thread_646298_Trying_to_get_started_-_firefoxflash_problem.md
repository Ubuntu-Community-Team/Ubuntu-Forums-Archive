---
title: "Trying to get started - firefox/flash problem"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by MTUser2007 on 2007-12-21
Hello,

I am typing this on a ThinkPad A31, a test to see if you can teach an old (50years) dog new tricks. I got Ubuntu installed, updated and managed to get wireless networking installed. I have email and the internet working through Firefox. However, I went to a flash based site and firefox asked to install a flash plug-in, I agreed and chose the Linux Gnash one over the  Macromedia one.

Either I did something wrong or there is Gnash plugin cannot render many sites correctly. I cannot get any of the flash menus on the home page at [www.netgear.com](www.netgear.com) to work. I cannot even see the page at [www.speedtest.net](www.speedtest.net). My thought was to uninstall the Gnash plug in and try the macromedia one, but I can't find out how to do that. I did find some long commands, but at my stage they mean nothing.

Suggestions, help, very much appreciated.

Chris

---

### Post by jan quark on 2007-12-21
this is something many people have problems with, just search the forum for flash problems. for me it worked to go to the official adobe page and install the newewst version of flash manually, 

just download the flash tar from this page
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
and follow the instructions, that is run the installar in the terminal. extract the downloaded file for example to you desktop.

then open the terminal, navigate to the folder and type      ```
michal@michal-laptop:~/Desktop/install_flash_player_9_linux$ ./flashplayer-installer 

```

then follow the instructions. Ask the forum if something goes wrong:)

---

### Post by mikewhatever on 2007-12-21
Gnash is open source, but still an alpha. It will not work with every site, that's the deal for now. Furthermore, the problem could be, that the site you visit requires IE.

---

### Post by MTUser2007 on 2007-12-21
Thanks for the help. I downloaded the plug-in from Adobe and followed the instructions. Viola! I can now see the flash based sites. I didn't even uninstall the Gnash product.

---


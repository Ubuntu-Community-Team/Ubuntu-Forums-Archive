---
title: "Flash Player Firefox plugin problem"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by hockeyfighter09 on 2007-12-09
I just reinstalled Ubuntu and when I go to a website that has flash on it the thing at the top pops up to show me to install the flash player. So I do it then it reloads the page but it didnt install correctly because the thing at the top comes back and the plugins on the website are missing.  What is the problem?

---

### Post by cotcot on 2007-12-09
Have you tried to install flashplugin-nonfree with synaptic ?

---

### Post by lswest on 2007-12-09
neither of those options worked for me, i had to go to the adobe site and download the plugin and manually install it, try through synaptic first though.

otherwise go [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux")
and download the tar.gz, then extract it to a folder and in that folder run "sudo sh flashplayer-installer" in the terminal to start the install.  the path to firefox is /usr/lib/firefox.

---

### Post by hockeyfighter09 on 2007-12-09
Yes, Ive uninstalled it with synaptics and installed it with it and also with the add/remove section to. It doesnt seem to change anything.

---

### Post by gakudva on 2007-12-09
I had the exact same problem described.  Thanks to this thread, direct download and install from Adobe website solved my problem.

regards, Ganesh

---

### Post by ingvildr on 2007-12-09
This has been known for a while and is fixed in hardy but for some reason its just not getting updated in gutsy. Seems like a pretty big drop of the ball since new users would have no idea why it doesn't work.

---

### Post by Myglaren on 2007-12-09
I found it worked perffectly with Hoary~Dapper~Feisty but not so much with Gutsy.  It works but for example doesn't draw the Youtube interface properly and when re-run the vidoe sticks but the music plays.

---

### Post by hockeyfighter09 on 2007-12-09
ok I downloaded it from Adobes site and made a folder in my home folder to extract it to.  But what do I type into the terminal to open the folder I saved it too so I can install it?

---

### Post by daradib on 2007-12-09
See [http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

---

### Post by Aglar on 2008-01-12
I've been having the same problem to, and have been trying to figure out how to fix it. I'll try the tarball.gz file from the Adobe site and see if that works.

---

### Post by pagubg on 2008-01-17
Hello, i have the same problem. Here is the solution:
Follow theese steps for installing the flashplugin-nonfree in Ubuntu Gutsy:

First, you need to close your browser!!!

```

# sudo aptitude purge flashplugin-nonfree; sudo aptitude install flashplugin-nonfree
# mkdir tmp; cd tmp; wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
# tar zxvf install_flash_player_9_linux.tar.gz
# cd install_flash_player_9_linux
# ./flashplayer-installer
# cd ../../ ; rm -rf tmp

```
When script ask you for the path where library will be installed, you can use this one for Mozilla Firefox like an example.
```

/usr/lib/firefox

```
Now, restart your favourite Mozilla Firefox browser and be happy :)

---

### Post by bazfull on 2008-01-18
Thanks to this thread a very newie has solved a problem. Many Many thanks:)

---


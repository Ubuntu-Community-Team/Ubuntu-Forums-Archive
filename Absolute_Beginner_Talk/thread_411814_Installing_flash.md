---
title: "Installing flash"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-04-17
I was trying to install flash plugins and got this error  :

"WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla
dir= /usr/lib/mozilla

I gave /usr/lib/mozilla but gets the same error again. I gave /usr/lib/opera and it says Opera not supported 

Why does things has to be sooo hard ? Anyone, please help !

---

### Post by lamalex on 2007-04-17
/usr/lib/firefox

---

### Post by tommcd on 2007-04-17
Search for flashplugin-nonfree in synaptic (make sure universe and multiverse repositories are enabled), or in terminal type:
sudo aptitude install flashplugin-nonfree

---

### Post by bla687 on 2007-04-17
I've been having trouble installing flash as well. I've tried using both methods outlined at this site: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) , but in both cases firefox still failed to recognize that the plugin was installed. Any suggestions?

---

### Post by Joseaa on 2007-04-17
I was finally able to install the plugin. Specifying the plugin path as /usr/lib/firefox did the trick here. 

Directory called "/usr/lib/mozilla"  do exist then why did the installer failed to install the plugins that directory ?

Why did the installer said "Opera is not supported" ? I copied the installed plugin files to Opera's plugin directory and it works fine in Opera also. 

As of now Linux looks like one big complex piece of puzzle. 

bla687, I followed the walkthrough mentioned in the adobe page : [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) and it works now.

---

### Post by camz on 2007-04-17
I always end up trying the hard way with everything on Ubuntu, but a very easy alternative was there. If you went to a site where Flash was needed, for example, a games site, when you try and load the game or whatever it is, a little puzzle sign will be on it instead of the media, and will say you need a plugin, click it, and you can install Flash in seconds INSIDE Firefox. :D

---

### Post by Joseaa on 2007-04-17
Camz, that sounds like a good solution but I think this method  works only with Firefox and not with Opera.( I haven't tested it, so not completely sure ) On the other hand, If I install it in your way, I wouldn't know where the plugin files are getting installed for me to copy it later to Opera's plugin folder.

---

### Post by camz on 2007-04-17
Okies. :D

---

### Post by Skardal on 2007-04-17
[Automatix]("http://getautomatix.com") should be mentioned, as this is a easy way to install flash, and many other common applications!

---

### Post by bla687 on 2007-04-17
Alright, here is my problem: So far, no tutorial has worked for my computer, including the one on the website to download the program, and using the puzzle piece thing in firefox also doesn't work. I realized this is because x86_64 architecture is not supported by this particular flash plugin. Any solutions?

Edit: Never mind, I found a way to do it here: [https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)

---

### Post by maluze on 2007-04-17
Hey guys...I too am having issues installing flash 9.0.31 to Opera 9.2 under Ubuntu. I tried linking to the firefox plugin: /usr/lib/opera/plugins, and now at first Opera will show flash media, then show a blank or say, "operapluginwrapper" has failed. As said previously, libflashplayer.so links to the firefox plugin, and under Opera:plugins, the flash plugin is mentioned...but i cant view flash..:confused: 

why cant Adobe support Opera in linux?? grrrrr :(

---


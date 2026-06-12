---
title: "Adobe flash player"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by slimstar on 2007-12-23
I have been trying to get flash payer to work to no avail
I have tryed going to a page and letting firfox tell me i need the plugin and install it that way, it will say restart firefox to take effect but it dont work..

i have tryed downloading it threw cmd line and it wont work

I tryed threw synaptic package manager and it dont work


I have tryed removing the downloaded package before doing all three of the above and my computer has all the updates...

I tryed to gnash and it came up but didnt play music... just showed a whte box where the music player would be

please make all instructions step by step and simple...

THANKS

---

### Post by carlchristopher on 2007-12-23
sorry not an answer but maybe a similar problem.
I am new to linux and cant seem to get the flash player to work. The instructions are not written for people who are only familiar with the big m.
PS is ther a "watch this tread" possibility in the forum?

---

### Post by LaRoza on 2007-12-23
> **carlchristopher said:**
> sorry not an answer but maybe a similar problem.
I am new to linux and cant seem to get the flash player to work. The instructions are not written for people who are only familiar with the big m.
PS is ther a "watch this tread" possibility in the forum?

You can subscribe to it.

This issue has been brought up many times, and there are several solutions. Search the forums for the threads.

---

### Post by NilsE on 2007-12-23
Try to do a "complete removal" in Synaptic and then try to install this deb file. Download it and open it with gdebi and let it install even though gdebi tells you there is one in the repo. Make sure FF is shut down when you install.

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

---

### Post by erfahren on 2007-12-23
there was a bug with flashplayer recently in Gutsy, but I thought it would be fixed by now. 

the flashplayer install only really consists of one file (libflashplayer.so). when you use Adobe's little installer it just puts that file in /usr/lib/firefox/plugins

When you install the flashplugin-nonfree package from Ubuntu it creates a directory: 
/usr/lib/flashplugin-nonfree
and puts the "libflashplayer.so" in there, then creates a symlink in /usr/lib/firefox/plugins linking to /usr/lib/flashplugin-nonfree/libflashplayer.so

I tell you all that because if there is another update released you know what's going on. And can undo this and install Ubuntu's package if you want. 

Anyway, if you have the flashplayer package installed right now go ahead and uninstall it again.

go to Adobe's site and download the new one from there. Save it to your home folder.

right-click on it and extract the archive (in the folder that was extracted you should see "libflashplayer.so")

now open the terminal (Applications > Accessories) and in there enter:
```

cd ~/install_flash_player_9_linux

```
then:
```

sudo mv libflashplayer.so /usr/lib/firefox/plugins

```


there is an alternative way to put that file in there...

open the terminal (Applications > Accessories) and in there enter:
```

sudo nautilus

```
the file browser should come up (and with root permissions so don't do anything crazy!)

then browse to /usr/lib/firefox/plugins and just copy and paste the "libflashplayer.so" file in there.

---

### Post by designzinthesun on 2007-12-23
This worked for me....

do a    flash player    search

find the thread that reads....

flash player
handsoffate

---

### Post by carlchristopher on 2007-12-23
""there is an alternative way to put that file in there...

open the terminal (Applications > Accessories) and in there enter:
Code:

sudo nautilus

the file browser should come up (and with root permissions so don't do anything crazy!)

then browse to /usr/lib/firefox/plugins and just copy and paste the "libflashplayer.so" file in there.""



Thank you that worked and was easy. Please never forget that we who come from the land of big m have no experience of anything technical
[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

---

### Post by SteveHill on 2007-12-23
To CarlChristopher
Thanks.  I am new to Ubuntu and your explanation on how to install the flash player was simple and It worked right off the bat for me.  Although you didn't explain which of the downloads on the Adobe site to use. I did have to do some searching to find out which of the Flash Players to download and really didn't get a diffiniative answer so I used the tar.gz and it worked.   What are RPM and YUM?  Thanks again.
Steve

---

### Post by erfahren on 2007-12-23
> **SteveHill said:**
> To CarlChristopher
Thanks.  I am new to Ubuntu and your explanation on how to install the flash player was simple and It worked right off the bat for me.  Although you didn't explain which of the downloads on the Adobe site to use. I did have to do some searching to find out which of the Flash Players to download and really didn't get a diffiniative answer so I used the tar.gz and it worked.   What are RPM and YUM?  Thanks again.
Steve
oh, I forgot that in my post as well, sorry! 

RPM and YUM are different packaging systems (kind of like our ".debs") for fedora, redhat, etc,

---

### Post by SteveHill on 2007-12-24
Now,  if I only new what "debs" ment. :).  Anyway,  I was wondering if you could lead me to a thread that would  have simple of instructions for me to figure out how to install java.  I like playing yahoo games but so far I haven't had any success with the various instructions on how to get it to work.  The instructions on navigating in the terminal have me lost after "click on terminal icon to open it".

Regards,
Steve

---

### Post by erfahren on 2007-12-24
> **SteveHill said:**
> Now,  if I only new what "debs" ment. :).  Anyway,  I was wondering if you could lead me to a thread that would  have simple of instructions for me to figure out how to install java.  I like playing yahoo games but so far I haven't had any success with the various instructions on how to get it to work.  The instructions on navigating in the terminal have me lost after "click on terminal icon to open it".


open up Synaptic Package Manager (under System) and search for the term "sun java". you should be able to find "sun-jav6-plugin" (also sun-java6-jre, etc.) but you just need to mark the sun-java6-plugin to install and it will automatically pull in the other packages it needs with it,

---

### Post by erfahren on 2007-12-24
> **SteveHill said:**
> Now,  if I only new what "debs" ment. ...
a ".deb" is a based on the Debian packaging system (Ubuntu is based on the Debian distro).

Anyway, I'm sure you've heard about sometimes needing to compile source in order to install a program. A .deb that is available for Ubuntu 7.10 (for example) has been pre-complied for that architecture and packaged so all you need to do is double-click on it to   install it (using the GDebi Package Installer. (which is the same as entering in "dpkg -i *name-of-package*.deb" into the terminal.)

---


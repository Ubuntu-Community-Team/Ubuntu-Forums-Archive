---
title: "How do I check version or uninstall  Adobe Flash Player?"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by tc101 on 2007-01-16
How do I check to see what version of Adobe Flash Player I have installed ?  It is causing me some problems.  If I want to uninstall it, how do I do that?

---

### Post by Obor on 2007-01-16
if you are using firefox put the following into the address bar
```
about:plugins
```
that should give you info about all the plug-ins you are using.

If you are using flash player 7 you should be able to remove it as follows:
```
sudo apt-get remove --purge flashplugin-nonfree
```

If you want Flashplayer 9 [here is how]("https://wiki.ubuntu.com/FlashPlayer9").

---

### Post by tc101 on 2007-01-16
Apparently I don't have have flashplayer installed because when I typed 
sudo apt-get remove --purge flashplugin-nonfree

I got this in the terminal:

tomcarr@tomcarr-desktop:~$ sudo apt-get remove --purge flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
tomcarr@tomcarr-desktop:~$

---

### Post by tc101 on 2007-01-16
My problem is that yesterday I was at this site 

[http://www.thaiair.com/](http://www.thaiair.com/)

and I clicked something that said I needed to click it to install flash player to see certain images.  The thing I clicked was one of those green firefox puzzle piece images.

After that, on another site which is more important to me, there are problems.  I want to uninstall whatever I installed yesterday, but I am not sure what it was.

---

### Post by tc101 on 2007-01-16
When I enter about:plugins in the firefox browser  this is what I see:

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Totem Web Browser Plugin 2.16.2

    File name: libtotem-basic-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.0 (compatible; Totem)

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by konst88 on 2007-01-16
You have flash 7 installed.
Do a search for libflashplayer.so and remove it.
Then install the flash 9.

---

### Post by tc101 on 2007-01-16
I found libflashplayer.so in a folder called install_flash_player_7_linux

When you say to remove it, can I just right click on it in nautilis file browser and send it to trash, or do I need to use the terminal.  If I need to use the terminal, is the correct syntax:

sudo rm /home/tomcarr/Desktop/install_flash_player_7_linux/libflashplayer.so

I should probably just try this and see what happens but I am new at this and nervous about breaking something and having to reinstall.

---

### Post by Obor on 2007-01-16
The one that you found looks like a download and not the actual plugin in the plugin directory. That folder is in your home folder therefore you don't need root rights to delete it.

I think you should be able to find all the firefox plugins in /usr/lib/firefox/plugins/ 
Have a look if its there. If you need to delete something there you can run nautilus as root (be careful) by 
```
gksudo nautilus
```

or delete it using terminal (change filename)
```
sudo rm /usr/lib/firefox/plugins/filename

```
 and then to install Flash 9 you can do as mentioned before

```
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz
tar -xzvf FP9_plugin_beta_112006.tar.gz
cd flash-player-plugin-9.0.21.78/
sudo cp libflashplayer.so /usr/lib/firefox/plugins/
```

---

### Post by tc101 on 2007-01-16
libflashplayer.so is not in /usr/lib/firefox/plugins

I think I have a problem with the nautilus search function, which is making it harder to locate all copies of libflashplayer.so.  Search does not seem to work when done from the root.  It works from any of the directories under the root, but not the root itself.  Is that the way it is supposed to work?

I am going to search each directory individually and will report back about any other copies of libflashplayer.so that I find.

---

### Post by tc101 on 2007-01-16
I think I used the wrong termonology when I said "Search does not seem to work when done from the root".  I should have said it does not work when done for the whole file system.

---

### Post by tc101 on 2007-01-16
I searched every directory except sys and only found ibflashplayer.so in the home directory.  When I try to search sys I get the wait symbol and the search never ends.

---

### Post by tc101 on 2007-01-17
I am still confused about removing an old version of flash player before installing the new version.  I can't find the installed version anywhere on my system.
I was told to look for libflashplayer.so but the only copy I see is in my home directory:

/home/tomcarr/Desktop/install_flash_player_7_linux/libflashplayer.so

I was told this looks like part of the install package and not the actual install.  

I tried to do a search with nautilus but I don't see it anywhere except where I mentioned in my home directory.

---

### Post by evaldas on 2007-01-17
I guess I know where you should look.

open terminal and:
```
$ cd ~/.mozilla/plugins
``` (there you'll find flashplayer.xpt and libflashplayer.so)
```
$ ls -al
```
remove those files (maybe it's enough to remove only libflashplayer.so, but I removed both)
```
$ rm *flash*
```
and then copy two files with the same names to that same directory from the file install_flash_player_9_linux.tar.gz (you'll need to extract those files from archive at first).

---

### Post by tc101 on 2007-01-17
That did it.  Thanks for your help.

---

### Post by Sasquatch2000 on 2007-01-19
> **tc101 said:**
> How do I check to see what version of Adobe Flash Player I have installed ? ...


Go to: [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

and it will tell you when you hold your mouse over the "About" tab thing.

---

### Post by Endolith on 2007-10-28
Ooh!  Getting rid of those two files removed the second listing from my about:plugins.   Let's see if reinstalling flashplugin-nonfree works!

---

### Post by Endolith on 2007-10-28
It worked!  Thank you!  :-D

---


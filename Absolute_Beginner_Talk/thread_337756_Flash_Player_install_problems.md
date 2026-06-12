---
title: "Flash Player install problems"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by SeaRox on 2007-01-13
I followed the wiki, here:
[https://wiki.ubuntu.com/FlashPlayer9?highlight=%28Flash%29%7C%28player%29](https://wiki.ubuntu.com/FlashPlayer9?highlight=%28Flash%29%7C%28player%29)
but it didn't work.  I think it might be that my Firefox is installed to a different directory.  I followed the wiki to install Firefox 2.0 also so I wouldn't think that would be the problem.  Any advice where to go from here?

---

### Post by moma on 2007-01-13
This command will tell you where the Firefox is installed to. (FF's installation directory).
[COLOR="SeaGreen"]echo $(dirname $(readlink -f $(which firefox)))[/COLOR]

So you can replace the last line (in the guide) with 
[COLOR="SeaGreen"]sudo cp libflashplayer.so  $(dirname $(readlink -f $(which firefox)))/plugins/[/COLOR]

And restart FF
$ [COLOR="SeaGreen"]killall firefox-bin [/COLOR]
$ [COLOR="SeaGreen"]firefox [/COLOR]

If you have installed FF in several locations, then ransack your system with
$ [COLOR="SeaGreen"]sudo updatedb [/COLOR]
$ [COLOR="SeaGreen"]locate  firefox-bin[/COLOR]
or just 
$ [COLOR="SeaGreen"]locate  firefox [/COLOR]

---

### Post by deanlinkous on 2007-01-13
anymore you should be able to just install flash automatically by visiting a site that requires flash and clicking on GET PLUGIN or whatever....

(flash is evil and should not be installed though....)

---

### Post by L Campbell on 2007-01-13
> **SeaRox said:**
> I followed the wiki, here:
[https://wiki.ubuntu.com/FlashPlayer9?highlight=%28Flash%29%7C%28player%29](https://wiki.ubuntu.com/FlashPlayer9?highlight=%28Flash%29%7C%28player%29)
but it didn't work.  I think it might be that my Firefox is installed to a different directory.  I followed the wiki to install Firefox 2.0 also so I wouldn't think that would be the problem.  Any advice where to go from here?


I think this might help you:-

[http://psychocats.net/ubuntu/flash](http://psychocats.net/ubuntu/flash)

---

### Post by ezsit on 2007-01-13
If you download the flash plugin directly from [www.adobe.com](www.adobe.com), you will have a file called install_flash_player_7_linux.tar.gz on your desktop. Right-click and extract here will produce a folder with the flash plugin and instructions. Follow the instructions and it should be OK.

During the installation, the installer will ask where you want to install the plugin, if you type:

/usr/lib/firefox  

(this is where mine is installed) as the destination, you should be fine. 

Hope this helps.

If the above location does not work, try:

/usr/lib/mozilla-firefox
or
/usr/lib/mozilla

Browse around the /usr/lib directory and see where firefox lives.

---

### Post by SeaRox on 2007-01-13
Thanks moma!  It was installed in /opt/firefox/ so that first line showed me where it was installed.  Followed the wiki with the new path and presto!  Worked like a charm.[http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

### Post by %hMa@?b&lt;C on 2007-01-13
use GNASH... I hate adobe

---


---
title: "How to play music/video/flash"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Steven201192 on 2007-06-30
I just got ubuntu and don't know ANYTHING about it and need to know how to install the stuff I need to watch videos, play music, etc.

---

### Post by gardara on 2007-06-30
For music try Amarok
For video try mplayer
For flash, install flash player for firefox.

Check out [http://ubuntuguide.org/](http://ubuntuguide.org/) it should help you installing these and another things :)

---

### Post by cotcot on 2007-06-30
Fun with linux is the choice you have. For video I have best results with "vlc".

---

### Post by Steven201192 on 2007-06-30
I need to install adobe flash player but I'm not sure how to install it. 

PS I'm still in windows mode

Now I just need to download the flash player. I downloaded the files from adobe but I don't really know what to do with them.

---

### Post by gardara on 2007-06-30
> **Steven201192 said:**
> I need to install adobe flash player but I'm not sure how to install it. 

PS I'm still in windows mode

Now I just need to download the flash player. I downloaded the files from adobe but I don't really know what to do with them.

look at my previous post, I pointed you to instructions at ubuntuguide.org

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

> sudo apt-get install flashplugin-nonfree

    * Restart Mozilla Firefox 

Note: if sound doesn't work in Flash Player (for example on YouTube):

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

    * Restart Mozilla Firefox. Now sound should work in Flash Player. 

---

### Post by Steven201192 on 2007-06-30
Thanks guys I've got it now :p

---


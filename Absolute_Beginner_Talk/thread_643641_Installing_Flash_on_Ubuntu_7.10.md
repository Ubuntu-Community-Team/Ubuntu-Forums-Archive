---
title: "Installing Flash on Ubuntu 7.10"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Fortune on 2007-12-18
I am having trouble installing adobe flash player on my Ubuntu 7.10 install. I googled it and found some instructions.

I first [Enabled Extra Repositories]("http://www.psychocats.net/ubuntu/sources") and then followed the steps listed in '[Installing Flash on Ubuntu]("http://www.psychocats.net/ubuntu/flash")'.

However, when I visit a site with flash (ie. Youtube), I still get the message 
> Additional plugins are required to display media on this page. 

When click "Install Missing Plugins" and try to install Adobe Flash Player, I get

> Package 'flashplugin-nonfree' is already installed

What am I doing wrong?

---

### Post by RomeReactor on 2007-12-18
Hi. There's a bug in the flashplugin-nonfree package; [this thread]("http://ubuntuforums.org/showthread.php?t=636397") has more information on it, as well as corrected packages. In short, you need to download this package for [32-bit Gutsy]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb"), or this one for [64-bit Gutsy]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb"). Once downloaded, just double click on the package to install it.

---

### Post by digital_sabotage on 2007-12-18
...make sure you've restarted your browser  ...then if it's still not working i'd try a shut down and restart ...otherwise not sure here ...gl

---

### Post by Fortune on 2007-12-18
Awesome. I've got it working. Thanks for your help guys.

---

### Post by Abripl on 2007-12-18
I just installed Ubuntu 7.10 and could not get the flash player to work irregardless of repositiories or restart. I went to Adobes download site for linux86 and downloaded their tar.gz package, followed their instructions and it worked. Go to their [_Linux86 download_]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux") site.

---

### Post by iamclueless on 2007-12-19
> **Abripl said:**
> I just installed Ubuntu 7.10 and could not get the flash player to work irregardless of repositiories or restart. I went to Adobes download site for linux86 and downloaded their tar.gz package, followed their instructions and it worked. Go to their [_Linux86 download_]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux") site.

can someone explain in newbie terms how to install it? Step 3 and 4 (download and unpack and executing) is a bit hard to follow

and finally, what do you do with the stuff in your desktop once its done its thing?

thanks

---

### Post by RomeReactor on 2007-12-19
> **iamclueless said:**
> can someone explain in newbie terms how to install it? Step 3 and 4 (download and unpack and executing) is a bit hard to follow

and finally, what do you do with the stuff in your desktop once its done its thing?

thanks

Hi. I suggest you give my previous post a try; if that doesn't work for you, then open a terminal, and navigate to where downloaded the **install_flash_player_9_linux.tar.gz** file. If the file is in your desktop:
```
cd Desktop
```
then:
```
tar -xvvzf install_flash_player_9_linux.tar.gz
```
```
cd install_flash_player_9_linux
```
```
sudo ./flashplayer-installer
```
and follow the instructions.

---

### Post by macogw on 2007-12-19
And if you're using Firefox (which I'm guessing you are), when it asks for the path, put 
/usr/lib/firefox

---

### Post by shuttleworthwannabe on 2007-12-19
I think there should be asticky for this; just the other day i posted this about installing flash [here]("http://ubuntuforums.org/showpost.php?p=3966230&postcount=1")

---

### Post by iamclueless on 2007-12-19
> **macogw said:**
> And if you're using Firefox (which I'm guessing you are), when it asks for the path, put 
/usr/lib/firefox

running firefox and opera.  will it make a difference?  ill do it for firefox and opera will cope? or for both?

thanks

---

### Post by iamclueless on 2007-12-19
yup never mind. it allows you to install to multiple browsers

i agree. sticky this until the automatic updates are out

---


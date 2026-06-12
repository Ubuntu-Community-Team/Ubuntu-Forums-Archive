---
title: "FireFox 2.0 installation"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2006-12-27
OK just finished installing Ubuntu 6.06.1 and after working out the username bug with some help from you guys ( thanks again by the way),everything seems to be working just fine. The look and feel of this distro is excellent. Now for the problem. Being a noobie to the nth power I need help in installing the Firefox 2.0 browser (update the 1.5 I have on the install), from the tar that I have downloaded. Do I have to do this from command line or is there an install wizard or the like used for this?  I am so new I don't want to try something and mess things up right off the bat. Thanks in advance and Happy New Year!!

---

### Post by deadgobby on 2006-12-27
Congrats on a good install. There is this.
[http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox)
and this
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
 Or you can upgrade to Eft with the new FF all ready there. Either way you may need to get the new flash player.
[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)
 The new flashplayer is good. 
Gobby

---

### Post by obsidion on 2006-12-27
> **jerrynewt said:**
> OK just finished installing Ubuntu 6.06.1 and after working out the username bug with some help from you guys ( thanks again by the way),everything seems to be working just fine. The look and feel of this distro is excellent. Now for the problem. Being a noobie to the nth power I need help in installing the Firefox 2.0 browser (update the 1.5 I have on the install), from the tar that I have downloaded. Do I have to do this from command line or is there an install wizard or the like used for this?  I am so new I don't want to try something and mess things up right off the bat. Thanks in advance and Happy New Year!!

  Sorry this is a command line method :) I works and is working fine for me with the same ubuntu well kubuntu in my case install.

  Ok fire up your terminal and cd to where you downloaded the tar, I suspect it is a tar.gz though.
ls to find the filename one you are in the directory, now sudo cp the file name /usr/local/share/
cd /usr/local/share
ls again tom make sure it's there now sudo tar zvxf thefilename enter
This will install to a firefox dirctory in that directory.

  Now you can use this a couple of ways, either call it directly from there to your desktop or menu or set up a symlink. If you want to set up a symlink. cd /usr/bin
sudo rm firefox this removes the symlink in that directory.

now sudo ln -s /usr/local/share/firefox/firefox enter

note the ln is a small Ln

 This should work fine, note that firefox 1.5x will still be in the system and plugins etc will need to be installed to the new plugin directory ie /usr/local/share/firefox/plugins to make them work.

Hope this helps

---

### Post by towsonu2003 on 2006-12-27
> **deadgobby said:**
> Or you can upgrade to Eft with the new FF all ready there.

Seeing that you just finished installing Dapper and you're new ;) , I wouldn't upgrade to edgy just yet. Settle and get used to it before redecorating your new house :mrgreen:

---

### Post by jerrynewt on 2006-12-27
Tried the psychocats.net proceedure and the 2.0 installation went so smoothly I thought there must be something wrong!! Worked like a charm--thanks a bunch for the tip.

---


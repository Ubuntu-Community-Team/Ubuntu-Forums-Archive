---
title: "Installing old VLC version on breezy"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by czk101 on 2006-09-12
Quick install guide:

sudo echo "deb [http://ubuntu.rootdir.de/](http://ubuntu.rootdir.de/) hoary universe" >> /etc/apt/sources.list
sudo echo "deb-src [http://ubuntu.rootdir.de/](http://ubuntu.rootdir.de/) hoary universe" >> /etc/apt/sources.list
sudo apt-get update
wget [http://www.rootdir.de/ubuntu/preferences](http://www.rootdir.de/ubuntu/preferences)
sudo cat preferences >> /etc/apt/preferences
sudo apt-get install vlc-plugin-alsa
[/quote]

When I run the final command i get the error message
> 
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distrobution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed. The following information may help to resolve the situation:

The following packages haveunmet dependencies:
vlc-plugin-alsa: Depends: vlc (= 0.7.2.final-3) but it is not going to be installed
E: Broken packages

Is there anything I can do to get round this?

Also, I downloaded vlc_0.7.2.final.orig.tar.gz from the site i mentioned above and tried to instal manually, but when i run the make command it tells me no targets specified and no makefile found.

I really want vlc 0.7.2 installed, so please help someone

cheers in advance

czk

---


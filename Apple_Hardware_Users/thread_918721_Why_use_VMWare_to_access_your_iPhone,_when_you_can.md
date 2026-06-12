---
title: "Why use VMWare to access your iPhone, when you can connect wirelessly with AirShare?"
date: 2008-09-13
forum: Apple Hardware Users
---

### Post by DayOldPorridge on 2008-09-13
Sorry if the title sounds like an advertisement.  I'm not the developer of the application, but I've found it to be a really simple way to transfer files to my iPhone, without having to download VMWare and get it all set up with a Windows desktop and then download iTunes on it, which would make my laptop lag even more than it does now.

It supports all filetypes supported by Safari, as well as Excel, OpenOffice, MS Word, .ogg, .wav, .m4a, mp3, .avi, C++ source code, perl, and various other formats listed in its manual.  Might even support .exe files; I haven't tried those yet.

To download it, go to App Store > Search: Air Sharing, and tap 'Free,' then 'Install.'

Then, if you tap on the AirShare icon on your home screen, it'll guide you through the steps to set it up.

But basically, you just go to **'Places > Connect to Server..,'** on Ubuntu, and select 'WebDAV' under Server Type, then type in the IP of your iPhone, (which is listed in AirShare set up manual, under **Connecting > Linux**.  Unless you're using KDE, don't type dav:// or http:// at the beginning of the address; it'll return an error if you do so) and under Port, type the last four numbers listed as the iPhone's IP address.  Most likely it'll be 8080.

And on KDE, you just open up Konqueror and type dav://<IP of your phone>:<port> (see the above paragraph).

At least it's a quick fix while the devs can figure out how to connect through USB with firmware 2.0.2.  I might even use this permanently, as there's no jailbreaking involved.

---


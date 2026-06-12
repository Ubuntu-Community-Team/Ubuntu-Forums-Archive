---
title: "Installing RealPlayer"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by slide4417 on 2006-09-27
To hear streaming audio, I got a popup that said I don't have an application to handle it. I downloaded RealPlayer 10 Gold for Linux. The download instructions told me to chmod a+x (permissions??) and then execute the file (./).
It started the install, but is asking me for the complete path I want it installed to...with no default.  Uh...C:/Program Files is all I was used to..   Where in Linux is suggested to install things like a media player??](*,) 
Thanks!

---

### Post by wieman01 on 2006-09-27
> /usr/local
...is one option. I prefer this one.

---

### Post by pseudonym on 2006-09-27
You sure you need Realplayer 10 to view that stream? I installed the Real version of Realplayer once (about a year ago) and found it slow to load and very invasive (like it is on Windows) with ads, popups and whatnot.

Since then I found it better to install a version of Realplayer that's been packaged for the distro. See [here]("https://help.ubuntu.com/community/RestrictedFormats") for more info on doing that.

Better still, many real streams will player in linux with the mozilla-mplayer plugin, assuming you are using firefox or mozilla browser. That's what I use these days, although the streams I view/listen to aren't made with the latest version of realplayer.

If you do go ahead with the Real Player you downloaded, the directory you should install it into is /usr/local  - designed for software you install outside of package management. Don't forget to run the installer as sudo , either.

---

### Post by deadgobby on 2006-09-27
i agree that realplayer mozilla plugin is the best to go. You can install it from Synaptic or 
[http://easyubuntu.freecontrib.org/index.html](http://easyubuntu.freecontrib.org/index.html)

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Gobby

---

### Post by nudnik on 2006-09-27
Real Player should go in /usr/bin, where totem, xmms, beep etc are located, amongst the executables. 

Installation is as follows:

download to desktop

chmod a+x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin


Answer in the affirmative to all queries except when you input /usr/bin

---

### Post by Marsolin on 2006-09-27
You could install the deb file for [Real Player]("http://linuxappfinder.com/package/realplayer") instead. Version 10 is in the dapper-commercial repository.

---


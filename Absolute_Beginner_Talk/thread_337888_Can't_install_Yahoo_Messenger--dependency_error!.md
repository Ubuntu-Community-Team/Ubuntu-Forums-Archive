---
title: "Can't install Yahoo Messenger--dependency error!"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-13
My son in law and I are trying to set up Yahoo Messenger on our comps but after downloading from the website (Debian version) we both get " Error: Dependency is not satisfiable : libssl0.9.6". Where do I get this or how do I fix the problem?? Any help is greatly appreciated!!

---

### Post by bg1256 on 2007-01-13
> **jerrynewt said:**
> My son in law and I are trying to set up Yahoo Messenger on our comps but after downloading from the website (Debian version) we both get " Error: Dependency is not satisfiable : libssl0.9.6". Where do I get this or how do I fix the problem?? Any help is greatly appreciated!!

Search in synaptic for it :)  Then just install it.

---

### Post by jerrynewt on 2007-01-13
There is no package for Yahoo Messenger in Synaptic under any header. Any more thoughts?? --we have tried everything and nothing seems to work. I have Gaim and am using it and can IM anyone using yahoo messenger just fine and vice versa. Don't know why yahoo is so important for son in law but that is the one he wants to use. Can't really understand though Gaim works just as well. Thanks again.

---

### Post by oyvindaa on 2007-01-13
I did a 

```
sudo apt-cache search libssl
```

in the terminal and found that libssl0.9.8 is the newest version.

Search for that in Synaptic and install it.

---

### Post by ENN0 on 2007-01-13
You know you dont need yaho mesenger..if u open gaim it will ask you for ur yahoo e-mail and password,once thats done all your contacts are availible...btw i dont know how to get the actual software runnig as i hate using the terminal myself:mad:

---

### Post by kliljedahl on 2007-01-13
I'm a Newbie too. Gaim only supports typing (which I hate). Gyachi (available if you install Automatix) has Webcam and microphone capability. There is an alternate program for the MSN Messenger also. Gaim is lame, IMO.

---

### Post by ashmew2 on 2007-01-17
Ive been facing a whole lotta problems in file transfer using Gaim , it wont recieve files from Windows Clients and when it sends file , 90% of time it transfers the whole file from this end but the other guy doesnt even get an accept thingy to start transfer...

---

### Post by TrashmanL on 2007-08-14
libssl0.9.8 is already installed on my machine and I still got the same error. 

I use GAIM, and it's nice sometimes, but it just doesn't have all the features of the full messenger, and other programs usually hog resources. I can't find an easy installer for Gyachi, and I don't think it'll be worth it since it only does Yahoo and nothing else. In fact, it doesn't seem to do anything more than the real Yahoo Messenger, so why would I use it instead? GAIM at least has multiple clients.

Anyone found a solution for this yet? I'd try to install the old version, then reinstall the new, but I can't find the package for 0.9.6, I can find 0.9.7 and 0.9.8.

---

### Post by mac71 on 2007-08-14
Why not try having a look at this:

[http://gyachi.sourceforge.net/download.shtml](http://gyachi.sourceforge.net/download.shtml)

Its a Yahoo client which works pretty much like yahoo 7. Oh, and go for the ubuntu edgy .deb file

---

### Post by TrashmanL on 2007-08-15
OK, I managed to do a workaround. I actually created my own Debian Package to install it. 

I used this page to help me:

[http://www.ibm.com/developerworks/linux/library/l-debpkg.html](http://www.ibm.com/developerworks/linux/library/l-debpkg.html)

It's a stupid little text file inside the package that needs to be changed, but I couldn't find a way to change it in the package itself, so it consisted of opening the package in GDeb (which you can install from Add/Remove) and extracting the files manually to a folder. This gave me two .tar.gz files: control.tar.gz and data.tar.gz. I extracted the files inside of them using fileroller. The files in control.tar.gz had to go into a folder called DEBIAN and the files in data.tar.gz just needed to go in the folders it creates itself (./opt/ymessenger). I put the Debian folder and the /opt folder into a folder called ymessenger_1.0.4_1_i386patch

I edited the text file control in the DEBIAN folder. I changed libssl0.9.6 to libssl0.9.8 in the dependencies. After I did that, I had a problem with xlibs. xlibs was not an available package in apt-get, and the only solution I could find was to delete the xlibs entry all together.

I installed build-essential and dpkg-dev using apt-get to be able to make my own package. I also installed libxft1 and xkb-data because that's what apt-get reported as the replacements for xlibs. 

Then I ran dpkg -b on the ymessenger_1.0.4_1_i386patch folder to create a ymessenger_1.0.4_1_i386patch.deb package. When I double clicked on it, it unpacked the files, but didn't run the Yahoo installer. I don't know why the Yahoo installer didn't run, but I manually ran /opt/ymessenger/bin/ymessenger (which was installed by the package) and it ran the Yahoo install program. Yahoo Messenger is now installed on my computer and appears to be working fine.

[B][SIZE="4"]
(Note: I did all of this logged in as root - I doubt I could've done all this as a regular user)[/SIZE][/B]

I also copied /opt/ymessenger/bin/yahoo_gnome.png to /usr/share/pixmaps to make the icon more accessible

Anyway, follow the above steps to create a package and install it. Alternately, after opening it with GDeb, you could, in theory, just copy the files inside over to a /opt folder and I'm sure it would work... but if its not installed as a package, Debian/Ubuntu won't keep track of it. Then again, I doubt in Yahoos next release that the new package would bother looking for an old one named ymessenger_1.0.4_1_i386patch. I guess I could've removed "patch" from the name and kept it the same... that might work for tracking purposes.

I'd like to post my patched package, but I'm worried that it may be against the Yahoo EULA and/or the rules of this Forum and I don't want to get booted. That, and it would probably give problems for people that didn't install the libxft1 and xkb-data packages before hand, since I couldn't get it to handle those dependenices (I tried adding libxft1 to the dependenices list, but it gave me an error when I did).

---


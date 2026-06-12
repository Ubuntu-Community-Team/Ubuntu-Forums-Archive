---
title: "Trouble with WINE configuration"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by jer4202 on 2006-04-23
When I try to configure Wine, I am getting an error message that I can't seem to figure out, and I can't find the answer. Please help! The following message is what I receive:

----------------------------------------------------------------
.......
.......
config.status: executing dlls/user/resources commands
config.status: executing dlls/wineps/data commands
config.status: executing include/wine commands

*** Warning: Freetype or Fontforge is missing.
*** Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished.  Do 'make depend && make' to compile Wine.



Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)
------------------------------------------------------------------------

Have any ideas? Thx in advanced.

---

### Post by htinn on 2006-04-23
I take it you're referring to the WineCVS [http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)

The configure step is missing a dependency. Make sure you'd didn't skip this step:

```
sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
```

---

### Post by jer4202 on 2006-04-23
[QUOTE=htinn]I take it you're referring to the WineCVS [/QUOTE]

Yes, I do, sorry for being unclear. I did not skip that step, I followed the instructions step-by-step from [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Wine]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Wine")
(except for the steps recquired to build from source). However when I did type in the code you gave me, it said the following..
```
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.7MB of archives.
After unpacking 49.3MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Get:1 http://wine.sourceforge.net binary/ wine 0.9.12~winehq1-1 [12.7MB]
Err http://wine.sourceforge.net binary/ wine 0.9.12~winehq1-1
  Error reading from server. Remote end closed connection
Failed to fetch http://wine.sourceforge.net/apt/binary/wine_0.9.12~winehq1-1_i386.deb  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
It said "maybe run apt-get update" and i did... still the same result. I dont know how to --fix-missing though

One thing I was concerned about is the location. I installed WINE through me@ubuntu:~$  but before I tyoe in sh WineCVS.sh I have to navigate to the desktop. Because it is in a seperate location, do you think it might effect it?

---

### Post by Bagnaj97 on 2006-04-23
Make sure you have everything installed from the ubuntu and programs sections here [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

---


---
title: "Xbmc Linux Port Install?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by ajgoyt on 2008-02-16
Hello I would like to try out XBMC on the linux port - I am at the WIKI and i have managed to get the latest SVN package on my hardrive etc- but i cannot seem to get XBMC running. any XBMC experts out there?

Stuck at this point on the Wiki.............

 How to run

Assuming you are in the XBMC source parent directory:

    * Link the userdata dir to UserData
          o #ln -sf userdata UserData 
    * Rename the file under media/Fonts/arial.ttf to media/Fonts/Arial.ttf
          o #mv media/Fonts/arial.ttf media/Fonts/Arial.ttf 
    * For using xbmcscripts installer (and perhaps more scripts):
          o #ln -sf scripts Scripts 
    * Execute the newly compiled binary:
          o # ./XboxMediaCenter 

    * If you'd like to run the executable from another directory for debugging purposes), set XBMC_HOME to where you have XBMC dist:
          o # XBMC_HOME=/home/whatever/XBMC
          o # export XBMC_HOME

---

### Post by ajgoyt on 2008-02-16
When i do this command Execute the newly compiled binary:
o # ./XboxMediaCenter   i get no file or directory...... Sorry kind of a noob to linux:)

---

### Post by con on 2008-02-22
I haven't ever installed it myself so can't help much. But you'd be much better off following the readme file instead of the wiki. Its much more up to date.

[http://xbmc.svn.sourceforge.net/viewvc/*checkout*/xbmc/branches/linuxport/XBMC/README.linux](http://xbmc.svn.sourceforge.net/viewvc/*checkout*/xbmc/branches/linuxport/XBMC/README.linux)

---

### Post by Mitch on 2008-02-22
I just installed this and it was pretty easy.

As the previous poster suggested look at the readme file.  In short do this:

```
sudo apt-get install make g++-4.1 gcc-4.1 libsdl1.2-dev libsdl-image1.2-dev libsdl-gfx1.2-dev libsdl-mixer1.2-dev libsdl-sound1.2-dev libsdl-stretch-dev libcdio6 libcdio-dev libfribidi0 libfribidi-dev liblzo1 liblzo-dev libfreetype6 libfreetype6-dev libsqlite3-0 libsqlite3-dev libogg-dev libsmbclient-dev libsmbclient libasound2-dev python2.4-dev python2.4 python-sqlite libglew1.4 libglew1.4-dev libcurl3-dev g++ gawk x11proto-xinerama-dev libxinerama-dev libxrandr-dev libxrender-dev libmms-dev pmount libmad0-dev libtre-dev libogg-dev libvorbis-dev libmysqlclient15-dev
```

in your svn xboxmediacenter direcotry do:

```
./build.sh
```

then: ```
cd BUILD
```
and:```
 ./xboxmediacenter 
```

This worked for me and xboxmediacenter has been surprisingly good--better than any other media center software that I've tried on Linux (elisa, mythtv, freevo).

---

### Post by swatF1RESTORM on 2008-03-05
I finally got everything installed but my video playback has a constant green tint while playing. I originally installed the 'debug' version (i.e. I had the "FreeMem" stuff at the top) and thought that may be the reason for the green tint... wrong. I recompiled the source using

```

 ./build.sh CONFIGOPT=--disable-debug CONFIRM

```

That got rid of the debug info but didn't help with the video playback. I also noticed that there were some problems with the XBMC for windows versions that was corrected by placing an ATI dll into the XBMC directory but I couldn't get that to work for linux. I put the dll in the XBMC folder as well as the default 'BUILD' folder, neither correcting the green tint problems?

I really want to avoid installing the ATI alt drivers because in the past (by my own hand or not) this causes my system to crash leaving me frustrated and starting from a fresh ubuntu install.

Any ideas?

---


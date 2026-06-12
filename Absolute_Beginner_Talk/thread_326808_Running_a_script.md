---
title: "Running a script"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Michaelt74 on 2006-12-28
Hi, Please could someone tell me how to run this script, step by step. I've just started using Ubuntu 6.1, so commands like chmod or sudos mean very little to me.

This is the script from a post in the forums:

[http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer](http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer)

The topic is how to make mplayer function. With this I start off by clicking on Applications>Accessories>Terminal> then what?

Thanks!

#!/bin/bash
if [ `id -u` != "0" ]; then
	echo "You should be root to run this script."
	exit 1
fi
apt-get install build-essential libpng12-dev libpng3-dev libgtk1.2-dev libgtkgl2.0-dev libgtkmm2.0-dev libgtk2.0-dev libwxgtk2.4-dev libx11-dev libxpm-dev libxt-dev firefox-dev
cd
mkdir mplayer-temp
cd mplayer-temp
wget [http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc1.tar.bz2](http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc1.tar.bz2)
wget [http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20061022.tar.bz2](http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20061022.tar.bz2)
wget [http://www.mplayerhq.hu/MPlayer/skins/clearplayer-0.8.tar.bz2](http://www.mplayerhq.hu/MPlayer/skins/clearplayer-0.8.tar.bz2)
wget [http://umn.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.31.tar.gz](http://umn.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.31.tar.gz)
tar -xf MPlayer-1.0rc1.tar.bz2
tar -xf essential-20061022.tar.bz2
tar -xf clearplayer-0.8.tar.bz2
tar -xf mplayerplug-in-3.31.tar.gz
mkdir /usr/local/share/mplayer/
ln -s /usr/share/fonts/truetype/freefont/FreeSans.ttf /usr/local/share/mplayer/subfont.ttf
mkdir /usr/local/share/mplayer/skins/
cp --recursive clearplayer/ /usr/local/share/mplayer/skins/
ln -s /usr/local/share/mplayer/skins/clearplayer/ /usr/local/share/mplayer/skins/default
mkdir /usr/local/lib/codecs/
cp essential-20061022/* /usr/local/lib/codecs/
cd MPlayer-1.0rc1
./configure --enable-gui
make -s
make install
cd ../mplayerplug-in
./configure
make -s
cp mplayerplug-in*.so /usr/lib/firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/firefox/components
cd
rm -rf mplayer-temp

---

### Post by evilghost on 2006-12-28
Open terminal.

Type these commands, exactly.
```

cd ~/
gedit myscript.sh

```

This will open gedit.  Now, copy and paste the script into gedit.  Save the script and exit gedit, which will return you to the terminal.

```

#!/bin/bash
if [ `id -u` != "0" ]; then
echo "You should be root to run this script."
exit 1
fi
apt-get install build-essential libpng12-dev libpng3-dev libgtk1.2-dev libgtkgl2.0-dev libgtkmm2.0-dev libgtk2.0-dev libwxgtk2.4-dev libx11-dev libxpm-dev libxt-dev firefox-dev
cd
mkdir mplayer-temp
cd mplayer-temp
wget http://www3.mplayerhq.hu/MPlayer/rel...1.0rc1.tar.bz2
wget http://www3.mplayerhq.hu/MPlayer/rel...061022.tar.bz2
wget http://www.mplayerhq.hu/MPlayer/skin...er-0.8.tar.bz2
wget http://umn.dl.sourceforge.net/source...in-3.31.tar.gz
tar -xf MPlayer-1.0rc1.tar.bz2
tar -xf essential-20061022.tar.bz2
tar -xf clearplayer-0.8.tar.bz2
tar -xf mplayerplug-in-3.31.tar.gz
mkdir /usr/local/share/mplayer/
ln -s /usr/share/fonts/truetype/freefont/FreeSans.ttf /usr/local/share/mplayer/subfont.ttf
mkdir /usr/local/share/mplayer/skins/
cp --recursive clearplayer/ /usr/local/share/mplayer/skins/
ln -s /usr/local/share/mplayer/skins/clearplayer/ /usr/local/share/mplayer/skins/default
mkdir /usr/local/lib/codecs/
cp essential-20061022/* /usr/local/lib/codecs/
cd MPlayer-1.0rc1
./configure --enable-gui
make -s
make install
cd ../mplayerplug-in
./configure
make -s
cp mplayerplug-in*.so /usr/lib/firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/firefox/components
cd
rm -rf mplayer-temp

```

Once you are back at the terminal type:

```

chmod +x myscript.sh
sudo ./myscript.sh

```

chmod +x will set the script, myscript.sh, as executable.  sudo (super-user do) will enable the script, myscript.sh, to be run as root (which appears to be one of the script requirements).

---

### Post by Michaelt74 on 2006-12-29
Thanks all, will let you know if I get it working!

---

### Post by ntlam on 2007-08-18
The last step didn't work for me. I couldn't install the plug-in

---


---
title: "Help with plugins"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by kokomonjo on 2007-12-23
Hi I am totally new to ubuntu and I found this tutorial for installing compiz plugins everytime it doesnt matter which plugin i try to install i get the same error at this one point and i was wondering if anyone could tell me what i am doing wrong and how i could go about fixing it.
I will paste a copy of the tutorial followed by pastes of what I do in terminal along with the error i get. 

**Tutorial:**

Install the packages required for compiling plugins:
Code:

sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool

Getting the plugin source tarballs
Make a compiz subdirectory in your home directory:
Code:

mkdir -p ~/compiz/

Use the following commands to download the plugins you want to install:
Code:

wget -O /tmp/3d.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugi ns/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef 3d21dbbb3'
wget -O /tmp/atlantis2.tar.gz 'http://gitweb.compiz-fusion.org/?p=users/smspillaz/atlantis2-0.6;a=snapshot;h=d50d17bcdef5a025699e6b1bc0d604a98 d1b74b2;sf=tgz'
wget -O /tmp/snow.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugi ns/snow;a=snapshot;h=01d0ff6ec71dae4699bc990e01145 69c8ad4e083'
wget -O /tmp/stars.tar.gz 'http://oreaus.googlepages.com/stars.tar.gz'
wget -O /tmp/atlantis.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugi ns/atlantis;a=snapshot;h=a47d7151444faccd66ea5cb88 4673cdebe5d7dff'
wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/s creensaver;a=snapshot;h=6565001eb389fb0d18cfead603 0054cc8edc6c5f'
wget -O /tmp/anaglyph.tar.gz 'http://oreaus.googlepages.com/anaglyph.tar.gz'
wget -O /tmp/wallpaper.tar.gz 'http://gitweb.compiz-fusion.org/?p=fusion/plugins/wallpaper;a=snapshot; h=c2d19686e46ae171b6a0c04da9de1adbd74ae8be'
wget -O /tmp/tile.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugi ns/tile;a=snapshot;h=550c91fa188efd39c9cea43f894b4 5716b5cc6d5'
wget -O /tmp/freewins.tar.gz 'http://oreaus.googlepages.com/freewins.tar.gz'
wget -O /tmp/fireflies.tar.gz 'http://oreaus.googlepages.com/fireflies.tar.gz'
wget -O /tmp/photowheel-0.6.tar.gz 'http://gitweb.opencompositing.org/?p=users/b0le/p hotowheel;a=snapshot;h=41d8090b55b629f72bef55d785b eaf468f31662f'


Extracting the source code

Example: For 3D Windows, you would do this:
Code:

tar -xf '/tmp/3d.tar.gz' -C ~/compiz/

This creates a directory at ~/compiz/3d.

Compiling a plugin after extraction
Switch to the directory created from extracting the tarball.

Example: For Freewins, you would do this:
Code:

cd ~/compiz/freewins-0.3-0.6

Once you are in the directory, you can compile the plugin:

Code:

make
make install

After compiling
Restart compiz and ccsm.

**And here is what I get after completing this tutorial:**

matt@kokomonjo:~$ sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-bcop is already the newest version.
compiz-dev is already the newest version.
build-essential is already the newest version.
libxcomposite-dev is already the newest version.
libpng12-dev is already the newest version.
libsm-dev is already the newest version.
libxrandr-dev is already the newest version.
libxdamage-dev is already the newest version.
libxinerama-dev is already the newest version.
libstartup-notification0-dev is already the newest version.
libgconf2-dev is already the newest version.
librsvg2-dev is already the newest version.
libdbus-1-dev is already the newest version.
libdbus-glib-1-dev is already the newest version.
libgnome-desktop-dev is already the newest version.
x11proto-scrnsaver-dev is already the newest version.
libxss-dev is already the newest version.
libxslt1-dev is already the newest version.
libtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matt@kokomonjo:~$ mkdir -p ~/compiz/
matt@kokomonjo:~$ wget -O /tmp/wallpaper.tar.gz 'http://gitweb.compiz-fusion.org/?p=fusion/plugins/wallpaper;a=snapshot; h=c2d19686e46ae171b6a0c04da9de1adbd74ae8be'
--11:02:56--  [http://gitweb.compiz-fusion.org/?p=fusion/plugins/wallpaper;a=snapshot;%20h=c2d19686e46ae171b6a0c04da9de1adbd74ae8be](http://gitweb.compiz-fusion.org/?p=fusion/plugins/wallpaper;a=snapshot;%20h=c2d19686e46ae171b6a0c04da9de1adbd74ae8be)
           => `/tmp/wallpaper.tar.gz'
Resolving gitweb.compiz-fusion.org... 195.114.19.35
Connecting to gitweb.compiz-fusion.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [  <=>                                ] 8,994         24.87K/s             

11:02:57 (24.83 KB/s) - `/tmp/wallpaper.tar.gz' saved [8994]

matt@kokomonjo:~$ tar -xf '/tmp/wallpaper.tar.gz' -C ~/compiz/
matt@kokomonjo:~$ cd ~/compiz/wallpaper
matt@kokomonjo:~/compiz/wallpaper$ make
linking   : build/libwallpaper.lalibtool: link: `build/wallpaper.lo' is not a valid libtool object
make: *** [build/libwallpaper.la] Error 1
matt@kokomonjo:~/compiz/wallpaper$ 

So as you can see I get some kind of error when I am supposed to give the make command. This happens on every one everything goes like i guess that  it should go then at the make command i get the error and of course I get an error at the make install command as well. It looks like this:

matt@kokomonjo:~/compiz/wallpaper$ make install
linking   : build/libwallpaper.lalibtool: link: `build/wallpaper.lo' is not a valid libtool object
make: *** [build/libwallpaper.la] Error 1
matt@kokomonjo:~/compiz/wallpaper$ 

Anyway help sorting this out would be appreciated. Thanks!

---

### Post by Moop on 2007-12-23
Do you have the build-essentials package installed?

---

### Post by kokomonjo on 2007-12-23
i am not sure. how do i install the build essential package?

---

### Post by kokomonjo on 2007-12-23
I just looked in synaptic package manager it said that i had it installed

---

### Post by seventhc on 2007-12-23
```
sudo apt-get install build-essential
```

edit..never mind then, i posted this and i guess you already looked while i was posting. :D

---

### Post by seventhc on 2007-12-23
Did you try it this way? you can enter make but when you do make install use sudo.
```

make
sudo make install
```also you might need to enter ```
 ./configure
``` before using ```
make
```
I usually ls the folder to see whats in it first, so if i see configure i use the configure command first, then make, then sudo make install

---

### Post by kokomonjo on 2007-12-23
tried the sudo make install command that didnt help this is what i tried. I am not sure if I did the ./confgure part correctly.

matt@kokomonjo:~$ cd ~/compiz/wallpaper
matt@kokomonjo:~/compiz/wallpaper$ ./configure
bash: ./configure: No such file or directory
matt@kokomonjo:~/compiz/wallpaper$ make
linking   : build/libwallpaper.lalibtool: link: `build/wallpaper.lo' is not a valid libtool object
make: *** [build/libwallpaper.la] Error 1
matt@kokomonjo:~/compiz/wallpaper$ sudo make install
linking   : build/libwallpaper.lalibtool: link: `build/wallpaper.lo' is not a valid libtool object
make: *** [build/libwallpaper.la] Error 1

---

### Post by seventhc on 2007-12-23
It looks like ./configure isn't needed here but I'm not to sure what you need. :(

---


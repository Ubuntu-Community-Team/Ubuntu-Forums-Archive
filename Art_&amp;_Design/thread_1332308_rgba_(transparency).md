---
title: "rgba (transparency)"
date: 2009-11-20
forum: Art &amp; Design
---

### Post by dzon65 on 2009-11-20
I posted this on the absolute beginners forum as well.So,I wonder how I can do this.How can I have the menubars (file,edit,image,go to,bookmarks....-bar)support transparency or rgba.Sorry for the bad picture.

---

### Post by VCoolio on 2009-11-20
You can choose:

1. Use compiz for window manager. Set visual effects to normal or extra. Install compizconfig-settings-manager (ccsm), then open it (system > preferences) and then under accessablitiy configure the Opacity, Brightness and Saturation plugin. Under opacity, set a value like this:
Menu | PopupMenu | DropdownMenu      80

2. Use xcompmgr-dana for window manager. The default xcompmgr doesn't support menu transparancy, so compile the former. It's not packaged for karmic yet and I also didn't check this on karmic, but I assume it will work.
First install compoling tools:
sudo apt-get install build-essential auto-apt checkinstall
Then install dependencies:
sudo apt-get build-dep xcompmgr 
Then download and compile xcompmgr-dana:
cd to the folder you wish (not being a system folder or you'll need sudo for every next command).
wget [https://launchpad.net/~crunchbangers/+archive/ppa/+files/xcompmgr-dana_1.1.4-0.1.tar.gz](https://launchpad.net/~crunchbangers/+archive/ppa/+files/xcompmgr-dana_1.1.4-0.1.tar.gz)
unpack and cd into the folder, then:
./autogen.sh
auto-apt run ./configure
make
sudo checkinstall

press yes, type a description you like and you're done. Run xcompmgr with the -m flag for menu transparancy, like so:
xcompmgr -cCfF -r7 -o.65 -l-10 -t-8 -D7 -m.80

3. Use the development version of the [murrine]("http://www.cimitan.com/murrine/") gtk2 engine, which will enable you to make everything transparant in gtk apps (not openoffice, firefox and some more). A howto is [here.]("http://janhouse.deviantart.com/art/Gnome-quot-Aero-look-quot-tutorial-142265951")

---

### Post by dzon65 on 2009-11-21
V.I read some of the tutorials and tried some stuff.But none of them seems to affect the browser,which was the goal in the first place.So I figured (newbie)if the menubar in the windows were transparent,this would make the FFmenu bar transparent as well (when it's set to the default theme).But I'll give this a try,one never knows.Thanks for the tips.

---

### Post by alex.rayu on 2009-11-21
RGBA needs also to be supported by the toolkits and apps you are using. That is why I await for a new GTK release with impatience. Some programs just plain dont support RGBA today.

---


---
title: "installing and removing prism"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2007-12-15
I think that i want to get mozilla's prism, however...
i found a site which told these instructions on how to get it, it said:

> 1. Download Prism 0.8 for Linux with the following commands in your terminal:

cd ~/Desktop/
wget [http://starkravingfinkle.org/projects/webrunner/prism-0.8-linux.tar.bz2](http://starkravingfinkle.org/projects/webrunner/prism-0.8-linux.tar.bz2)


2. Extract the tarball file to /opt/ folder:

sudo tar jxvf prism-0.8-linux.tar.bz2 -C /opt/

3. Now execute these commands:

sudo chown -R root:root /opt/prism/
sudo chmod -R 755 /opt/prism/


4. Create a menu:

sudo gedit /usr/share/applications/prism.desktop

Then add:

[Desktop Entry]
Encoding=UTF-8
Name=Prism
Comment=Prism
Exec=/opt/prism/prism
Icon=/opt/prism/chrome/icons/default/webrunner48.png
Terminal=false
Type=Application
Categories=Application;Network;
StartupNotify=true




that all seems pretty straightforward

however - what do i do if i want to remove it?

---

### Post by jken146 on 2007-12-15
The installation instructions just ask you to extract some files from an archive, copy them into /opt, change their ownership and permissions so you can run them, and create a desktop entry so you can launch the program easily.

To remove this, all you need to do is delete the files you created (everything in /opt/prism and the desktop entry file).  The commands would be:
```
sudo rm -R /opt/prism
```
and
```
sudo rm /usr/share/applications/prism.desktop
```

---


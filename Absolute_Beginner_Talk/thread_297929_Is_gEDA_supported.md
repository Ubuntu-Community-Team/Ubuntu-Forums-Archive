---
title: "Is gEDA supported?"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by pubairplanes on 2006-11-11
Hey all,
  Just deleted Windows 98 on my old comp and installed Edubuntu for the kids to use. 

Just wondering if the package gEDA would work on this? If so, what would be the best way to go about installing it?

Thanks.

---

### Post by chriscando on 2006-11-11
Have you looked for it in Synaptic? I use ubuntu and can install it using:
```
sudo apt-get install geda
```
in the terminal.

---

### Post by punx45 on 2006-11-11
ditto on the above..   according to the gEDA download page ([http://www.geda.seul.org/download.html](http://www.geda.seul.org/download.html))

---

### Post by pubairplanes on 2006-11-11
I did try to locate it in Synaptic, tried Apt-get as well. Neither worked...

When I try Synaptic I don't see it in the list of available packs
and...
When I try Apt-get it tells me "Reading package lists... Done
                                Building dependency tree       
                                Reading state information... Done
                                E: Couldn't find package geda"

BTW: I get this message whenever I try to install any package through apt-get. Maybe its due to my wirless setup???

Thanks

---

### Post by punx45 on 2006-11-11
you probably need to add extra repositories (places synaptic looks for programs) Ubuntu starts with a default (and safe) list of repositories, and for most third party etc. programs you need to add repositories.

---

### Post by Sef on 2006-11-11
[Enable]("https://wiki.ubuntu.com/AddingRepositoriesHowto") the universe and multiverse repositories, then you should be able to download gEDA.

---

### Post by punx45 on 2006-11-12
further info on repositories:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by pubairplanes on 2006-11-12
That did it punx and sef, Thanks!

---

### Post by Sef on 2006-11-12
You're welcome, pubairplanes.  Please ask if you have any more questions.

---

### Post by pubairplanes on 2006-11-12
Ok, I installed the package and all of its suggested packages through Synaptic. At the end of the install it said it completed successfully, but the program does not appear in any of my menus (Applications, Places, or System) So were do I go to access the actual program? :oops: 

Thanks.

---

### Post by Phatfiddler on 2006-11-14
In terminal, type:

```
geda
```

for the main control panel for it, but if you are installing through synaptic or apt-get, it will NOT install the entire suite, and will need some configuration edits before it will work properly.

Visit [http://www.geda.seul.org/]("http://www.geda.seul.org/") for the complete suite and documents etc.  Some have had success by installing via an ISO available for download from the geda site.

Look at these other posts if you need help
[http://www.ubuntuforums.org/showthread.php?t=222906&highlight=geda]("http://www.ubuntuforums.org/showthread.php?t=222906&highlight=geda")
[http://www.ubuntuforums.org/showthread.php?t=282040&highlight=geda]("http://www.ubuntuforums.org/showthread.php?t=282040&highlight=geda")

---

### Post by Adrian Nania on 2006-12-04
If you installed gEDA thru synaptic, to start geda the quick and dirty way, open a terminal and type:
geda
Otherwise, you need to create some shortcuts on your desktop.

---

### Post by Adrian Nania on 2006-12-04
If you installed gEDA thru synaptic, to start geda the quick and dirty way, open a terminal and type:
geda
Otherwise, you need to create some shortcuts on your desktop. You can use something like:
```
echo To start gEDA, create a Launcher to /home/programs/gEDA/bin/geda on your desktop
rm -rf /home/programs/gEDA/geda.start
rm -rf $HOME/Desktop/gEDA.desktop
cat >>/home/programs/gEDA/geda.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/geda
EOF
chmod +x /home/programs/gEDA/geda.start
cat >>$HOME/Desktop/gEDA.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/geda.start
TryExec=
Icon=/usr/share/pixmaps/gnome-ccperiph.png
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=gEDA
GenericName[en_CA]=gEDA
Comment[en_CA]=
Name=gEDA
GenericName=gEDA
Comment=
EOF
```
You should identify the PATH for each application and substitute in my example.

---


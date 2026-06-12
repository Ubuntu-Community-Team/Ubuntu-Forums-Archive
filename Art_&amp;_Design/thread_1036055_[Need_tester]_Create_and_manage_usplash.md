---
title: "[Need tester] Create and manage usplash"
date: 2009-01-10
forum: Art &amp; Design
---

### Post by philarmonie on 2009-01-10
After discussion in the french ubuntu forum, a new software has been created: usplash-manager.
This soft allows users to create and manage their usplash themes.
Since this is still a beta version we need testers to debug the soft and see if it works correctly.
For the moment we can only create a new theme and install it as default used theme. When the program will be finished, the users could also download usplash in site such gnome-look and manage their usplash theme installed on disk.
For the moment, the GUI is in gtk (after there will also be a GUI in qt for kde users) and in french. If someone could give me a link to a tutorial on how to manage internationalisation in python, I will write it in english too. So I hope that non french users could understand the differents options to set (Image for the background, colors for the progress bar and the text, positions of the differents elements...)

The project is hosted on launchpad, to get it you have to install bzr
```
sudo apt-get install bzr
```
Then to download the sources code:
```
bzr branch lp:usplash-manager
```
This last command will download all the sources code and put in an 'usplash-manager' directory
Then to launch the software:
```

cd usplash-manager/usplash-manager-gui-gtk
sudo python UMPorject.oy

```

There is no 'make install' method or '.deb' package, since this project is very young. We will add it when the soft will be consider enough stable.

I hope this soft will enjoy you and help you to create usplash theme easily.

Philarmonie.

---


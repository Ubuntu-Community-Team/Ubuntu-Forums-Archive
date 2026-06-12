---
title: "Problem installing Firefox 1.5"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2006-01-11
Hello guys,
I wanted to change the theme for firefox (current version 1.0.2) but i was asked to upgrade it to version 1.5 so i downloaded the file "firefox-1.5.tar.gz".
now i'm not sure how to install this package:
I tried  sudo dpkg -i firefox-1.5.tar.gz 
but just how i spected i got this error message:

dpkg-deb: `firefox-1.5.tar.gz' is not a debian format archive
dpkg: error processing firefox-1.5.tar.gz (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 firefox-1.5.tar.gz

i'm still kind of new with ubuntu..
so if anyone could give  a hand, i would appreciate it.

---

### Post by kaamos on 2006-01-11
Look here: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by tkjacobsen on 2006-01-11
You have downloaded a source package. You have to unpack it, then compile it and finally install. First you have to install the build tools:
```
sudo apt-get install build-essential
```
then unpack:
```
tar xvzf firefox-1.5.tar.gz
```
cd into the new directory. Configure firefox:
```
./configure
```
If some depencies is missing, you have to install them using apt-get install.
Then compile
```
make
```
Finally install:
```
sudo make install
```
Then your new firefox should be up and running

---

### Post by aysiu on 2006-01-11
I'm curious as to why you have Firefox 1.0.2 installed. Are you using Warty? If so, your terminal may be in Applications > System Tools > Terminal.

If you're using Breezy, however, it's in Applications > Accessories > Terminal.

The terminal is where you type all the commands. I would advise you to copy and paste them instead of retyping them.

Please follow these directions:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

tkjacobsen's directions are general ones for .tar.gz files, but the Wiki instructions actually make sure that when you launch *firefox* the new version will pop up instead of the old version.

---

### Post by poloman2 on 2006-01-11
As far as i know i have Hoary 5.04.....

---

### Post by aysiu on 2006-01-11
[QUOTE=poloman2]As far as i know i have Hoary 5.04.....[/QUOTE] If you have Hoary, the terminal is in Applications > System Tools > Terminal

---

### Post by poloman2 on 2006-01-11
Thank you guys it worked....
Now how do i create a icon to start  it??

---

### Post by aysiu on 2006-01-11
[QUOTE=poloman2]Thank you guys it worked....
Now how do i create a icon to start  it??[/QUOTE] If you followed the Wiki instructions, the regular Firefox icon (a blue globe, possibly) should start it. Otherwise, you can just right-click on the panel and create a launcher with the command ```
firefox
``` If that doesn't work, try ```
mozilla-firefox
```

---


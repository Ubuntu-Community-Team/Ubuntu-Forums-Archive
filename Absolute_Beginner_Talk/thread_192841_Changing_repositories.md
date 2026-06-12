---
title: "Changing repositories"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by DesignerX on 2006-06-09
On upgrading from hoary to breezy instructions it says :
#
Change your repositories to look for Breezy
     From
         URI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
         Distribution: hoary
         Sections: main restricted

      To
         URI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
         Distribution: breezy
         Sections: main restricted

Do I need to go over all the binaries and sources appearing at the repositories screen and change from hoary to breezy or there is a single place to do that for all ?

thx.

---

### Post by Beej on 2006-06-09
Not sure what you mean, but if you go to a terminal and type

sudo gedit /etc/apt/sources.list

it should bring up your sources list. If you press ctrl f, to bring up the find dialogue and click the replace tab you should be able to put hoary in the find an breezy in the replace. Click replace all.

Save and exit. 

then from terminal type 

sudo apt-get update

then sudo apt-get dist-upgrade

---

### Post by xyz on 2006-06-09
Hi-
If you run ```
 sudo gedit /etc/apt/sources.list

```, you'll see a window with all your sources.
In the right-hand corner of that window (right next to "Paste"), you'll see an arrow pointing downward. Click on it and then again on "Replace". In "Search for", type 'hoary' and in "Replace with", type 'breezy'. Finally, click on "Replace".

In short, hoary will be replaced with breezy wherever it needs to be in just a couple of clicks. I think this is what you're looking for?

And then update/upgrade!

OOOps! sorry...this is called simultaneous. Good weekend to you guys.

---


---
title: "how can i downgrade compiz?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by shoagun on 2006-08-16
I have been running xgl+compiz for a month now.  Today I did an update and now the effects are slightly different.  I liked the way compiz worked before.  How can I go back?

---

### Post by BitTorrentBuddha on 2006-08-16
[Here](http://www.beerorkid.com/compiz/archives/) is a list of all quinn packages, download, extract and dpkg whichever version you want, to see the version you'll have to hover over the link and check the status bar. One of these is most likely what you want to downgrade to though.
[quinn30](http://www.beerorkid.com/compiz/archives/quinndebs-compiz_0.0.13-0quinn30.tar.gz)
[quinn29](http://www.beerorkid.com/compiz/archives/quinndebs-compiz_0.0.13-0quinn29.tar.gz)
[quinn28](http://www.beerorkid.com/compiz/archives/quinndebs-compiz_0.0.13-0quinn28.tar.gz)

---

### Post by shoagun on 2006-08-16
sorry, could you explain this a little?  i just want to make sure i don't do something that will mess up compiz all together.

---

### Post by BitTorrentBuddha on 2006-08-17
Depending on which version you which to downgrade to, download that tarball to your home folder. To extract the files double click the tarball. It should spit out 2 or 3 files, to install the files, extract them into your folder and then open up a terminal and run this command if you are using GNOME (Ubuntu):```
sudo dpkg -i compiz_*.deb compiz-gnome*.deb
``` And if you are using KDE (Kubuntu) the furthest forward you can go is [quinn28](http://www.beerorkid.com/compiz/archives/quinndebs-compiz_0.0.13-0quinn28.tar.gz), but run... ```
sudo dpkg -i compiz_*.deb compiz-kde*.deb
```

---

### Post by aeiah on 2006-08-17
if its only the effects that are different, are you sure you cant just change some settings? after one update, i had to change the settings for the cube zoom and mouse corner hotspots back to how they were before. if you are unhappy with the newer version because it's buggy on your system, then thats a different matter

---

### Post by shoagun on 2006-08-17
What's the best way to change the settings?  Here is what I don't like:

-When I rotate the cube, it pulls back first and then rotates.  And roation is slower

-When I zoom in and then move to the edges, I can't see down the side of the cube.  It's like looking at just a flat screen.

---

### Post by BitTorrentBuddha on 2006-08-17
The zoomin' cube can be fixed by setting /apps/compiz/plugins/rotate/screen0/options/zoom to 0 (it's default is two.) and I can still see the sides of my cube, I just have to zoom in 2 steps instead of one. This can be 'fixed' by setting /apps/compiz/plugins/zoom/screen0/options/step to 3. 

You can choose to edit these with gconf-editor, or just type these two commands into a terminal.```
gconftool -t float -s /apps/compiz/plugins/zoom/screen0/options/step 3
gconftool -t float -s /apps/compiz/plugins/rotate/screen0/options/zoom 0
```

---

### Post by shoagun on 2006-08-17
BTB, thanks so much!  I was completely ignorant of the ease of changing compiz settings.  Now I have it working just  like I like it.

---


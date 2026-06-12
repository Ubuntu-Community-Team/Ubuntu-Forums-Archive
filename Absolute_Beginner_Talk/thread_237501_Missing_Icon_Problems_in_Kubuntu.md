---
title: "Missing Icon Problems in Kubuntu"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by 6and9.42 on 2006-08-16
Not sure what I did, but i seemed to have scrambled the default icons ](*,) and now some number of icons in different places are showing up as white squares no matter which icon set I use.

I was installing icon sets and I think I mistakenly removed the default icons folder. I have the following "crystal" folders in icons:

crystal
Crystal
crystalsvg

Is there somewhere I can download the original/default icon set?

Thanks a ton! :)

---

### Post by Jucato on 2006-08-16
The default icon theme used by Kubuntu is the Crystal SVG icon theme. I'm not really sure which specific package holds the whole theme, but you could try these alternatives:

1. Download the Crystal SVG theme from KDE-Look.org and install it
2. Reinstall the package *kubuntu-desktop*.
```
sudo apt-get install --reinstall kubuntu-desktop
```

Hope that helps a bit.

---

### Post by phossal on 2006-08-16
As an alternative, you might try installing the "default" icons for Mozilla/Firefox. This will install the "real deal" firefox icons.

Do as follows: (#, is a command prompt)
1. # sudo gedit ~/icons
2. copy and paste the following into the document:

# GET FIREFOX/MOZILLA ICONS
wget -c -O /tmp/mozilla-firefox.png [http://www.cs.cornell.edu/~djm/ubuntu/mozilla-icons/mozilla-firefox.png](http://www.cs.cornell.edu/~djm/ubuntu/mozilla-icons/mozilla-firefox.png)
wget -c -O /tmp/document.png [http://www.cs.cornell.edu/~djm/ubuntu/mozilla-icons/document.png](http://www.cs.cornell.edu/~djm/ubuntu/mozilla-icons/document.png)
chmod 644 /tmp/mozilla-firefox.png /tmp/document.png
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/icons/default.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/icons/document.png
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
sudo cp /tmp/mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.png
sudo cp /tmp/mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.xpm
sudo cp /tmp/mozilla-firefox.png /usr/lib/mozilla-firefox/icons/default.xpm
sudo cp /tmp/document.png /usr/lib/mozilla-firefox/icons/document.png
sudo cp /tmp/mozilla-firefox.png /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm

2. Save and close the document.
3. # chmod +x ~/icons
4. # sh ~/icons
5. Restart/open Firefox

---

### Post by phossal on 2006-08-16
Then check this out..

[http://www.cs.cornell.edu/~djm/ubuntu/](http://www.cs.cornell.edu/~djm/ubuntu/)

---

### Post by 6and9.42 on 2006-08-16
Thanks for the help guys :) Unfortunately, it didn't work. However, I've discovered that if I reinstall just the applications with the missing icons they come back. I'm still not sure what happened. Oh well, thanks again.

edit: phossal, thanks for the detailed help, though the problem was system-wide, not just firefox

---


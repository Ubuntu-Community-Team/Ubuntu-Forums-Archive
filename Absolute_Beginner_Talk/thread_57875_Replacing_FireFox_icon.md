---
title: "Replacing FireFox icon?"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by Nate_Benton on 2005-08-18
Can you replace the FireFox icon with the newer icon of FireFox? It looks cooler :(

---

### Post by rama on 2005-08-18
[QUOTE=Nate_Benton]Can you replace the FireFox icon with the newer icon of FireFox? It looks cooler :([/QUOTE]
 You may want to read this 
[http://www.ubuntuforums.org/showthread.php?t=34354](http://www.ubuntuforums.org/showthread.php?t=34354)
 
And also check this 
[http://www.ubuntuforums.org/showthread.php?t=53050](http://www.ubuntuforums.org/showthread.php?t=53050)

---

### Post by Vorian on 2005-08-18
[QUOTE=Nate_Benton]Can you replace the FireFox icon with the newer icon of FireFox? It looks cooler :([/QUOTE]

Here you go

```
wget -c http://frankandjacq.com/ubuntuguide/mozilla-firefox.png
wget -c http://frankandjacq.com/ubuntuguide/document.png
chmod 644 mozilla-firefox.png
chmod 644 document.png
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/icons/default.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/icons/document.png
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.png
sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.xpm
sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/icons/default.xpm
sudo cp document.png /usr/lib/mozilla-firefox/icons/document.png
sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
```

---


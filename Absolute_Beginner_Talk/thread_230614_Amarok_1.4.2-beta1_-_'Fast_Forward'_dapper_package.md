---
title: "Amarok 1.4.2-beta1 - 'Fast Forward' dapper package"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Sir_Yaro on 2006-08-06
= The following extra functionalities are included:
 =   + xine-engine
 =   + XMMS Visualization Wrapper
 =   + MySql Support
 =   + Konqueror Sidebar
 =   + MusicBrainz Support
 =   + MP4/AAC Tag Write Support
 =   + iPod Support (with Artwork)
 =   + iRiver iFP Support
 =   + Creative Nomad Jukebox Support
 =   + Advanced Tag Features
 =   + Dynamic Collection

link: [1.4.2-beta1 - 'Fast Forward'](http://yaro.gdi.pl/cclick/click.php?id=19)

other useful packages:
[http://yaro.gdi.pl/deb/](http://yaro.gdi.pl/deb/)

---

### Post by orb9220 on 2006-08-06
I have 1.4.1 installed do I have to uninstall?
Or can I just install this package.

Thanks for the link.

---

### Post by Sir_Yaro on 2006-08-06
yes, you must uninstal packages amarok-xine, amarok-engines, amarok by:
```
sudo dpkg -r amarok-xine amarok-engines amarok
```
then just install this package

---

### Post by orb9220 on 2006-08-06
Thank You kindly Sir!

---

### Post by anandrd on 2006-08-09
I am getting this error when I run amarok after installing your deb file-

amarokapp: symbol lookup error: /usr/lib/libamarok.so.0: undefined symbol: _ZN9KLineEdit13focusOutEventEP11QFocusEvent


and then it crashes.

---

### Post by orb9220 on 2006-08-09
Yes wouldn't run for me either. Had to rollback to 1.4.1

---

### Post by pimlottc on 2006-08-16
I got the same error.  I'm now using the Kubuntu Amarok 1.4.1 packages for dapper ([http://kubuntu.org/announcements/amarok-1.4.1.php)](http://kubuntu.org/announcements/amarok-1.4.1.php)).

---

### Post by geearf on 2006-08-17
I had no problem running it :)
But it's not that better, and it removed kubuntu-desktop so no more upgrades :(

---

### Post by citizenkeith on 2006-08-23
> **orb9220 said:**
> Yes wouldn't run for me either. Had to rollback to 1.4.1

Same here. :( I appreciate Sir Yaro's efforts nonetheless. I'm glad others are able to use it.

How are the new features? I'm especially interested in Dynamic Collection, the lack of which is the single most frustrating thing about Amarok, IMHO.

---

### Post by geearf on 2006-08-25
Didn't get much, and I lost kubuntu-desktop, therefore I went back to the ubuntu's version.

I'm waiting for the final release.

---

### Post by geearf on 2006-08-25
Actually it's now, so now let's reload kubuntu.org for a while :)

---


---
title: "How do you install Adobe Flash Player?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-12
Alot of the sites I enter, needs to have Adobe Flash Player installed. How do I install this?

---

### Post by Perfect Storm on 2006-07-12
Download the linux version.
Extract it to your Desktop.

then:
```
cd Desktop && install_flash_player_7_linux
sudo sh flashplayer-installer
```

---

### Post by tommcd on 2006-07-12
You can just do this:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
Just make sure you have universe and multiverse repositories enabled.

---

### Post by james016 on 2006-07-12
I downloaded it from Adobe's site. Extracted the files and in the terminal navigated to where the files are and typed in ```
sudo ./flashplayer-installer
```

It will ask where your browser is which is /usr/lib/mozilla-firefox

Type that in and it installs

---


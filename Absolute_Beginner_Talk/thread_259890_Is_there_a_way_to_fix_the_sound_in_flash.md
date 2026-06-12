---
title: "Is there a way to fix the sound in flash?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-09-18
If I'm playing music and I go to a site like YouTube or any other site that has sound nothing will play until I close both FireFox and Amarok, and reopen  FireFox. Is there a way to fix that?

---

### Post by WalmartSniperLX on 2006-09-18
I dont know much about that problem but I do know that flash 7 for linux has its problems. In example, the sound/video sync is a little off timing. 

Lol sorry thats all i know or have to say. :D  sorry if that isnt much ](*,)

---

### Post by Amablue on 2006-12-14
Still, months later I've never got this problem solved. Anyone have any other insights?

---

### Post by macogw on 2006-12-14
Did you try installing the Flash 9 beta?

---

### Post by Sef on 2006-12-14
Are you using Dapper, Edgy, or other?  And Ubuntu, Kubuntu, or other?  What are your system specs?

---

### Post by Amablue on 2006-12-15
> **macogw said:**
> Did you try installing the Flash 9 beta?

I don't think I've messed with any of the flash settings or versions, so unless it was auto-installed with the updater I'm using whatever I got with Ubutnu

> **Sef said:**
> Are you using Dapper, Edgy, or other?  And Ubuntu, Kubuntu, or other?  What are your system specs?

Ubuntu Edgy, on a Dell Inspiron 2200. What specs are you looking for? I can't remember most of the stuff off the top of my head.

---

### Post by sivnik on 2006-12-15
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

```
FIREFOX_DSP=""
```

To:

```
FIREFOX_DSP="aoss"
```

Restart Mozilla Firefox. Now sound should work in Flash Player. 

from this: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by Amablue on 2006-12-15
Okay, I did that and it's still the same as before. The sound works up until something else stars playing music, usually Amarok.

---


---
title: "flash player not working in Firefox"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by wiesiek_h on 2007-03-24
Hi,
I am a relatively new linux user. I installed Edgy 6.10 a couple of weeks ago on a IBM laptop A31 2652. I'm having problems playing flash on youtube, etc.. via firefox.  Here's the unique part, I have the flash player installed & working fine on one user profile, however I can not get it to work on another. 
I checked firefox preferences & java & java scripts are all enabled. 

Any help will be appreciated..

---

### Post by r4ik on 2007-03-24
Did you try,

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Muzik83 on 2007-03-24
The plugins for firefox can be in two places, either a "user" plugin which is only available for that single user (this is probably what you have), and a "global" plugin, which is available to all users.

Did you install the flash plugin from the Adobe installer, or from the ubuntu repository?  If you installed it from the Adobe one, try running it as root and installing the file to /usr/bin/firefox/plugins 

Alternatively you could copy /home/<user>/.mozilla/plugins/libflashplayer.so to /usr/bin/firefox/plugins to enable it for every user.

Hope this helps

-sean

---

### Post by psycosmyth on 2007-03-24
> **Muzik83 said:**
> The plugins for firefox can be in two places, either a "user" plugin which is only available for that single user (this is probably what you have), and a "global" plugin, which is available to all users.

Did you install the flash plugin from the Adobe installer, or from the ubuntu repository?  If you installed it from the Adobe one, try running it as root and installing the file to /usr/bin/firefox/plugins 

Alternatively you could copy /home/<user>/.mozilla/plugins/libflashplayer.so to /usr/bin/firefox/plugins to enable it for every user.

Hope this helps

-sean

Souds like it to me, I did the same. I reinstalled into the global folder.

---

### Post by aysiu on 2007-03-24
Muzik83 is correct that there are two types of Flash installation--local and global.

The link r4ik posted will help you uninstall locally (for one user) and install globally (for all users).

---

### Post by whiskeysquared on 2007-03-25
Okay, I can **play** flash, but it's (searching for the term) "jumpy" and the audio cuts in and out.  I'm pretty sure I read that a flash player is a recent addition to Ubuntu, is it still just in a buggy phase or should it run flawlessly?  It's really cutting into wasting time watching documentaries on Google Video...

---


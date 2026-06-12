---
title: "Program Edit Boot Up Options"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-05-31
I remember using it a long time ago, it allowed me to tick which options I wanted at boot up, Boot Up is taking a very long time, but I believe it's because it's pausing and looking around for my internet when I'm on a wireless connection (which is applied after I login)

Does anyone know of the program? and how to install?

---

### Post by Billy McCann on 2007-05-31
There's one called Boot Up Manager.  May be what you're looking for.

sudo aptitude install bum

---

### Post by Ek0nomik on 2007-05-31
You can also edit your user program loading by going to:

Preferences/Sessions

Or, here are some links describing some processes that are loading on boot:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

---

### Post by chris062689 on 2007-05-31
I looked at BUM, and that seems only to be for startup programs.
How can I turn off stuff like loading bluetooth, looking for internet connection, etc
at boot up (when the ubtuntu splash screen is being displayed and the orange bar is moving across the screen)

---

### Post by Billy McCann on 2007-06-05
There's a program called rcconf in the repos.  This will do part of what you're wanting.  

To not load bluetooth on boot, create a /etc/modprobe.d/my_blacklist file and add "blacklist bluetooth" to this file.  

```
sudo nano /etc/modprobe.d/my_blacklist
```

[quote=my_blacklist]blacklist bluetooth[/quote]

I can't remember how to keep from searching for internet connection.  There's a file to edit, of course.  Can't remember exactly but it's something like /ect/??????/interfaces or such.  If you can find the file I'm talking about, you can comment out the interfaces that you'd like to keep from being searched for.  Like, if you use dial-up, you can comment out eth0 and be done with it.

---


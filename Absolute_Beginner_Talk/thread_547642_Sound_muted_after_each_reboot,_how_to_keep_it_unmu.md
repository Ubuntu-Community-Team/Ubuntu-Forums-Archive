---
title: "Sound muted after each reboot, how to keep it unmuted?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by sahra on 2007-09-10
I've been having a lot of sound problems on my Acer Aspire 5052AWXMi.   Sound now works, but I have to unmute it after every reboot by going into alsamixer to turn on surround sound in order for my speakers to work.  Therefore I have no start-up noise, etc.

Could someone please help me to figure out how I can fix this so that 'surround' is not set to mute every time I turn my computer on?  Thanks.

---

### Post by BrendanM on 2007-09-10
I've seen this before. I'm not sure why it happens. I had good luck by on the login screen, going to Options, then clicking "Select Session" and choosing GNOME instead of "Last Session" and then when it asked me, I made that the default.

Don't ask me why that made any difference.

---

### Post by sahra on 2007-09-10
Thanks for your suggestion, but unfortunately there's no change. :( 

I suspect this isn't the case, since I seem to have tried in all ways possible, but is there a specific order I need to do that in, eg resetting the surround settings in alsamixer and then changing my session or vice versa?

---

### Post by rsambuca on 2007-09-10
After unmuting your sound in a session, try entering this command in a terminal. I have no idea if this will work in ubuntu, but it worked for my gentoo installation.```
sudo /etc/init.d/alsasound save
```

---

### Post by thecure on 2008-02-18
> **rsambuca said:**
> After unmuting your sound in a session, try entering this command in a terminal. I have no idea if this will work in ubuntu, but it worked for my gentoo installation.```
sudo /etc/init.d/alsasound save
```


I'm having the same problem after latest update to Hardy. I'll try your tip after I get home. Thank you.

---


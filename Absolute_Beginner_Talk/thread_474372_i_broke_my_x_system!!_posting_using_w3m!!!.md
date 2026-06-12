---
title: "i broke my x system!! posting using w3m!!!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by richieboy on 2007-06-15
i added firestater to the startup menu and 
now my x won't boot up.  my boot 
music plays but the screen stays 
on the crosshatch pattern and my 
desktop won't come up.  please help!!!!
thanks,
rich
also first time using vim without a helping web page open.

---

### Post by NinerSevenTango on 2007-06-15
I can't help you but I'll be watching because I was just thinking about installing that myself.

In fact, I would have done it already if I didn't spend hours on another little glitch.

--97T--

---

### Post by zvacet on 2007-06-15
```
sudo /etc/init.d/gdm restart
```

if no luck 

```
sudo dpkg-reconfigure xserver-xorg
```

and this doesn´t help try to remove firestarter

```
sudo apt-get --purge remove firestarter
```

---


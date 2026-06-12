---
title: "How do I schedule tasks?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by jgrabham on 2007-08-02
Preferably with a GUI

And can I make them open in a specific workspace?

---

### Post by apswartz on 2007-08-02
In Kubuntu you would use Kcron. I would imagine that Gnome has a similar program, but I don't know what it would be.

---

### Post by jgrabham on 2007-08-02
> **apswartz said:**
> In Kubuntu you would use Kcron. I would imagine that Gnome has a similar program, but I don't know what it would be.

It seems to be working under gnome, but cant remember where all the programs are saved on the drive :/

---

### Post by apswartz on 2007-08-02
Most of the program executables (or links to the executables) will be in the /usr/bin directory

---

### Post by apswartz on 2007-08-02
For other programs try using the locate command...
```
sudo updatedb
locate programname
```

If that gives you too many results try something like...
```
locate programname |grep bin
```

The grep command will search for the word that follows it in the results.

---

### Post by jgrabham on 2007-08-02
When I try to save I get

An error occurred while updating crontab

---

### Post by apswartz on 2007-08-02
Do you have the Silent box checked? If so, clear it and try saving again.

---

### Post by jgrabham on 2007-08-02
> **apswartz said:**
> Do you have the Silent box checked? If so, clear it and try saving again.

Yes, but doesnt matter; found a gnome program called schedule

---


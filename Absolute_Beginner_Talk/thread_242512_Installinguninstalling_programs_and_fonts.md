---
title: "Installing/uninstalling programs and fonts"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by bombitmd on 2006-08-23
Since I can't access the Internet when using Ubuntu (I have a winmodem and no cash yet to buy an external), I can only download stuff while in XP and save the downloads in my /home directory.  So far, I've noticed that most updates or downloads for Linux is done thru apt-get, but you have to be connected.

1. Is there a way around this?  Is there a way to download updates first, and then install in Ubuntu?  If so, what command lines should I type in?  Is there a program that will do the install for me, similar to Windows' Install Shield?

2. How do you UNinstall?

3. How do you install fonts?

I wish Ubuntu could do something to fix this winmodem issue. :(  So much is dependent on an Internet connection.  

Is there a generic driver our there for Conexant chipsets?  I guess I'll have to settle for the 14.4 limit of the free driver from Linuxant... unless someone can help me out. :(

---

### Post by mlind on 2006-08-23
> **bombitmd said:**
> 
1. Is there a way around this?  Is there a way to download updates first, and then install in Ubuntu?  If so, what command lines should I type in?  Is there a program that will do the install for me, similar to Windows' Install Shield?
[/code]

2. How do you UNinstall?

3. How do you install fonts?

I wish Ubuntu could do something to fix this winmodem issue. :(  So much is dependent on an Internet connection.  

Is there a generic driver our there for Conexant chipsets?  I guess I'll have to settle for the 14.4 limit of the free driver from Linuxant... unless someone can help me out. :(


1. Yes.
```

sudo dpkg -i *package.deb*

```

2. To remove a package you should use apt-get, aptitude or maybe synaptic. aptitude has deprecated apt-get. All these should work
```

#Remove, but leave global configuration files
sudo aptitude remove *package*

#Or, remove package fully 
sudo aptitude purge *package*

#Remove package only, but don't touch its dependencies. Useful if just want to temporarily uninstall package without uninstalling the dependencies
sudo dpkg -P --force-depends *package*

```


Have you tried searching existing threads about your winmodem issue? I think you'll find your answer this way.
For example: [http://www.ubuntuforums.org/showthread.php?t=198730&highlight=winmodem](http://www.ubuntuforums.org/showthread.php?t=198730&highlight=winmodem)


/edit
3. put those to ~/.fonts or /usr/share/fonts I guess. For global fonts, you may have to run
```

sudo dpkg-reconfigure fontconfig

```

---

### Post by bombitmd on 2006-08-23
Thanks! At least I'm learning bit by bit.  And yeah,  I've searched the forums regarding winmodem.  I'll read the link you mentioned, although I don't know if it applies to Conexant chipsets.

---

### Post by mlind on 2006-08-23
How about these links ?
[http://www.ubuntuforums.org/showthread.php?t=36091&highlight=conexant](http://www.ubuntuforums.org/showthread.php?t=36091&highlight=conexant)
[http://www.ubuntuforums.org/showthread.php?t=190728&highlight=conexant](http://www.ubuntuforums.org/showthread.php?t=190728&highlight=conexant)

---


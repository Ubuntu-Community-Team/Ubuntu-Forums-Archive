---
title: "Uninstall Wine Tools"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by jrjr on 2006-08-20
.

---

### Post by mlind on 2006-08-20
WineTools includes file called **INSTALL.txt**, which says that running **./uninstall** on the directory where you extracted the archive should do the job.

---

### Post by jrjr on 2006-08-21
.

---

### Post by jrjr on 2006-08-21
.

---

### Post by jrjr on 2006-08-21
.

---

### Post by jrjr on 2006-08-21
.

---

### Post by mlind on 2006-08-21
> **jrjr said:**
> Thanks for that but it doesnt seem to work

In a terminal I cd'ed to winetools
I typed ./uninstall and got this:

```
bash: ./uninstall: No such file or directory
```

There is nothing called uninstall in the winetools directory

Did I not do something right?
In my last Ubuntu install, there was an uninstall in the winetools directory, I remember seeing it. I used the same install procedure this time too or so I thought

The uninstall file is on the directory where you extracted winetools archive and execute ./install in the first place.

Consider using .deb packages or installing packages locally for easier maintenance in the future.

---

### Post by jrjr on 2006-08-21
.

---

### Post by mlind on 2006-08-21
> **jrjr said:**
> There is a directory called winetools-0.9jo-III right next to wine tools. I entered that dir in terminal and executed ./uninstall

Version: winetools-0.9
Release: 0.9
Uninstalling translations . . .
./uninstall: line 15: cd: /usr/local/winetools/po: No such file or directory
ls: *.po: No such file or directory
Uninstalling WineTools from /usr/local/winetools . . .
rm: cannot remove `/usr/local/bin/wt': No such file or directory
rm: cannot remove `/usr/local/bin/winetools': No such file or directory
rm: cannot remove `/usr/local/bin/findwine': No such file or directory
WineTools has been uninstalled.

Both directories are still there in my /home dir with all of the stuff inside of them as if no uninstaller was ever run

It doesn't uninstall it from your $HOME directory, but from /usr/local. ./install script you executed earlier installed winetools to /usr/local (hopefully). Check that /usr/local doesn't contain anything winetools related. You can use **slocate *winetools*** (run **updatedb** first) or
```

find /usr/local -name '*wine*'

```
This only finds files containing *wine* on their name, so there could be a lot of other files left behind.

This is one reason why Debian packages are preferred. Install and uninstall  are easier and actually work. I wouldn't execute any rogue install scripts requiring root privileges on my system.

---

### Post by jrjr on 2006-08-21
.

---

### Post by mlind on 2006-08-21
> **jrjr said:**
> I did a **LOT** of reading prior to using this method. Wine tools are inherently fragile and more often than not are troublesome. The method I choose to pursue sounded to me like it had the most chance of success. I actually did have IE and Dreamweaver working once but that was not my goal. 

Believe me, I will never use this method again unless I absolutely have to!!
I guess this is a lesson learned eh? I'm heading to do what you just said to do.... but what about the winetool dirs in my home dir? Just delete them?


Thanks for helping me out  :)

You can remove winetools from your $HOME directory, its contents was just used for installing. There are methods to test archives like this on a sandboxed environment without doing any damage to your system.

But lesson learned I'm sure ;)

---

### Post by jrjr on 2006-08-21
.

---


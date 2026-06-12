---
title: "Opera?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by blanc11 on 2006-06-04
Can I find Opera in a Repository anywhere? If not how do I install it?

---

### Post by adwait on 2006-06-04
Yes you can find it, you need to enable all the repos for that (look @ my sig). To install either use Adept/Synaptic or in the terminal type
```
sudo apt-get install opera
```

Alternatively, if you want the opera 9.0 beta, then go to their website and download the .deb file. After downloading, double click it or use
```
sudo dpkg -i <filename>
```

---

### Post by johso on 2006-06-04
This page describes how to do it both via dpkg and apt-get.
[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)
I recommend the apt-get way, because you'll then be able to update it from within the Update Manager when a new version is released.
Should be just about what you need.

Alternatively you could use Automatix:
[http://ubuntuforums.org/showthread.php?t=177646&highlight=automatix](http://ubuntuforums.org/showthread.php?t=177646&highlight=automatix)

---

### Post by blanc11 on 2006-06-04
Ok, Thanks

---

### Post by Ensnared on 2006-06-04
Add the following to your /etc/apt/sources.list:```
deb http://deb.opera.com/opera etch non-free
```
You can use any repository from [http://deb.opera.com/](http://deb.opera.com/) - it's pretty much the same version of the browser for all of them as far as I know.

After you've added it, do```
sudo apt-get update
```...followed by:```
sudo apt-get install opera
```...or, if you want the statically linked one, do:```
sudo apt-get install opera-static
```

---

### Post by blanc11 on 2006-06-04
is there a version available for Dapper yet?

---

### Post by Ensnared on 2006-06-04
[QUOTE=blanc11]is there a version available for Dapper yet?[/QUOTE]
The instructions I posted work for Dapper. I installed it that way myself.

---

### Post by MattCarp on 2006-06-05
[QUOTE=Ensnared]The instructions I posted work for Dapper. I installed it that way myself.[/QUOTE]


I get:

The following packages have unmet dependencies:
  opera: Depends: xlib6g (>= 3.3.6) but it is not installable or
                  xlibs but it is not installable
E: Broken packages

It looks like xlibs-dev needs to be installed, which also installs a slew of *-dev packages.

---


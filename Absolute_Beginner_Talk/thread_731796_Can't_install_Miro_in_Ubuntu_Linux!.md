---
title: "Can't install Miro in Ubuntu Linux!"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-03-22
First of all, thank god to the PCLinuxOS Magazine, because Miro was featured there.

[http://pclosmag.com/html/Issues/200803/page03.html](http://pclosmag.com/html/Issues/200803/page03.html)

Hopefully there's an Ubuntu Magazine too, since I use Ubuntu. Wondering why you don't have a binary or a ready-to-install package of Miro for PCLinuxOS, while in Ubuntu, you have one, but only available to Repositories.

Anyway I added the download site to the APT-Sources or Repositories' list of Ubuntu, then I got this message:

```
karlo@karlo-laptop:/etc/apt$ sudo apt-get install miro
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  miro: Depends: libxine1 (< 1.1.8) but 1.1.10-1~gutsy1 is to be installed
E: Broken packages
karlo@karlo-laptop:/etc/apt$
```

**WHY?**

---

### Post by aidanr on 2008-03-22
The one in the Ubuntu repository hasn't been updated yet, try using [Miro's repository]("http://www.getmiro.com/download/ubuntu.php").

---

### Post by karlo on 2008-03-22
> **aidanr said:**
> The one in the Ubuntu repository hasn't been updated yet, try using [Miro's repository]("http://www.getmiro.com/download/ubuntu.php").

I figured, why not install it using the Synaptic Package Manager, the GUI version of APT-GET instead of using APT-GET via Terminal.

Still, I receive the following error message, just please check out the screenshots.

---

### Post by jan quark on 2008-03-22
try to run

```
sudo dpkg --configure -a
sudo apt-get install -f
```

any error messages?

---

### Post by karlo on 2008-03-22
> **jan quark said:**
> try to run

```
sudo dpkg --configure -a
sudo apt-get install -f
```

any error messages?

I'll try to run them, but a question, what are those commands? What do they do?

**Anyway**, I ran those commands. No error results.

---

### Post by jan quark on 2008-03-22
these commands should resolve unmet dependencies and half installed packages
but strangely enough there are no problems with that as it seems...

---

### Post by zvacet on 2008-03-22
```
gksudo gedit /etc/apt/sources.list
```

add line 

deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/

save and close

```
sudo apt-get update
```


and you will have latest Miro in synaptic.

---

### Post by karlo on 2008-03-22
> **jan quark said:**
> these commands should resolve unmet dependencies and half installed packages
but strangely enough there are no problems with that as it seems...

I've tried doing all of the installing steps again. I still receive the following message: see the screenshots.

---

### Post by jan quark on 2008-03-22
found this

[http://ubuntuforums.org/showthread.php?p=4565080](http://ubuntuforums.org/showthread.php?p=4565080)

---

### Post by vamsibethapudy on 2008-06-12
I think the problem is solved. i have upgraded & the upgradation removed miro for some reason.
I just went to the miro site & copied the ftp link given in another forum & reloaded. i used add or remove programs & miro is installed.

---


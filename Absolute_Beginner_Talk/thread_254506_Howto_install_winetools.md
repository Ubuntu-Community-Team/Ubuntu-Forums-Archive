---
title: "Howto install winetools"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-09-10
I can't get winetools to install.  I've gone to the winetools directory. The install instructions say:  To install WineTools extract the archive in a temporary directory and call
"./install" as user "root". WineTools will get installed at
/usr/local/winetools.

I have gone to terminal and typed su ./install.  It comes back with the  error message.... Unknow id: ./install

So what am I doing wrone?  I thought as long as was in the correct directory that the su command would do the install.  But I quess I am wrong. Doesn't root mean that makes temporarly a super user?

---

### Post by dbd on 2006-09-10
The problem is that you are using the wrong command, instead you should type:
sudo ./install

su is used to log in as another user, see "man su"
sudo is the command to execute a single command as root, so thats the one you want to use.

---

### Post by jbumgar on 2006-09-10
Thanks DBD!! That did it!

---

### Post by leveliv on 2006-11-08
> leveliv@leveliv-desktop:~/Desktop/winetools-0.9jo-III$ sudo ./install
sudo: ./install: command not found


help thats what I got... when I sudo ./install

---

### Post by leveliv on 2006-11-09
I got it ..there was an extra DIR so it was 
> :~/Desktop/winetools-0.9jo-III/**winetools-0.9jo-III**$ sudo ./install ](*,) ](*,)

---

### Post by BLTicklemonster on 2006-11-09
How did setting it all up go? I'm having problems galore.

---

### Post by nkayesmith on 2007-01-04
> **BLTicklemonster said:**
> How did setting it all up go? I'm having problems galore.

What kind of problems? I can try to fix them...

---

### Post by marx2k on 2007-01-30
My problems is after installing the most current wine, then installing Winetools, I try to run wt

and I get:
```

no suitable Wine directory found...
Wine 0
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0".

```

And then it tells me I dont have a current version of Wine available

---

### Post by nkayesmith on 2007-01-30
> **marx2k said:**
> My problems is after installing the most current wine, then installing Winetools, I try to run wt

and I get:
```

no suitable Wine directory found...
Wine 0
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0".

```

And then it tells me I dont have a current version of Wine available

See [http://ubuntuforums.org/showthread.php?t=149585&page=43](http://ubuntuforums.org/showthread.php?t=149585&page=43)

---


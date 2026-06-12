---
title: "Monopod"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by YumZ on 2006-02-18
I'm not very good at installing apps from the source, and I have monopod-0.2.tar.gz sitting on my desktop all lonely.  I unpacked it and "./configure" in the terminal but I'm missing mono apparently.  So I installed that, but it still won't work.  Any one know what I need to do?

---

### Post by cilynx on 2006-02-18
Try installing mono-devel and libmono-dev.

Whenever you are compiling from source and it complains that you don't have something, you need to install [whatever]-dev  

Good Luck

---

### Post by YumZ on 2006-02-19
Ok, i configured it, then I did "make," and this came up:

```
make[2]: Nothing to be done for `install-exec-am'.
/bin/sh ../mkinstalldirs /usr/local/lib/monopod
mkdir /usr/local/lib/monopod
mkdir: cannot create directory `/usr/local/lib/monopod': Permission denied
make[2]: *** [install-monopodSCRIPTS] Error 1
make[2]: Leaving directory `/home//Desktop/monopod-0.3/Monopod'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home//Desktop/monopod-0.3/Monopod'
make: *** [install-recursive] Error 1
```

---

### Post by cilynx on 2006-02-19
It's trying to write some scripts to /usr/local/lib.  That's probably not a bad thing, but it needs root privileges.  Try 'sudo make'.

---

### Post by YumZ on 2006-02-19
Ok, Monopod Podcast Client shows up under the Sound & Video menu, but clicking on it does nothing.

---

### Post by appdx on 2006-02-20
I'm trying to install this, i got to sudo make install without any problems...here is the terminal output
```
sudo make install
Making install in Monopod
make[1]: Entering directory `/home/appdx/Desktop/monopod-0.2/Monopod'
make[2]: Entering directory `/home/appdx/Desktop/monopod-0.2/Monopod'
make[2]: Nothing to be done for `install-exec-am'.
/bin/sh ../mkinstalldirs /usr/local/lib/monopod
mkdir /usr/local/lib/monopod
 /usr/bin/install -c Monopod.exe /usr/local/lib/monopod/Monopod.exe
/bin/sh ../mkinstalldirs /usr/local/bin
 /usr/bin/install -c Monopod /usr/local/bin/Monopod
make[2]: Leaving directory `/home/appdx/Desktop/monopod-0.2/Monopod'
make[1]: Leaving directory `/home/appdx/Desktop/monopod-0.2/Monopod'
make[1]: Entering directory `/home/appdx/Desktop/monopod-0.2'
make[2]: Entering directory `/home/appdx/Desktop/monopod-0.2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/appdx/Desktop/monopod-0.2'
make[1]: Leaving directory `/home/appdx/Desktop/monopod-0.2'
appdx@Titan:~/Desktop/monopod-0.2$ monopod
bash: monopod: command not found
appdx@Titan:~/Desktop/monopod-0.2$ cd ~
appdx@Titan:~$ monopod-0.2

```
It doesn't appear in any menus either, can anyone help?

---

### Post by cilynx on 2006-02-20
```

/usr/bin/install -c Monopod.exe /usr/local/lib/monopod/Monopod.exe

```

Mono is a little wonky compared to normal Linux binaries.  That line tells us that it installed the main executable for Monopod into /usr/local/lib/monopod/.  That's not a normal place for an executable, and thus isn't in our default path.  Also, mono executables require an interpreter.  Try:
```

mono /usr/local/lib/monopod/Monopod.exe

```
See where that get's you...

---

### Post by appdx on 2006-02-20
'Cannot stat 'Monopod.exe': no such file or directory.

---

### Post by cilynx on 2006-02-20
If you go look in that directory, is there anything there?

---

### Post by YumZ on 2006-02-20
/usr/bin/install: cannot stat `Monopod.exe': No such file or directory

Monopod.exe is in /usr/local/lib/monopod/.  Clicking on it comes up with this: Couldn't display "/usr/local/lib/monopod/Monopod.exe".

---


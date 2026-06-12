---
title: "install problem"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by binary_dream on 2006-11-05
Hi folks,

I'm having a problem with installing avast anti virus on my edgy.
I followed this thread: [http://ubuntuforums.org/showthread.php?t=229128](http://ubuntuforums.org/showthread.php?t=229128)

```

sudo dpkg -i file_name.deb

```

this went fine, but then this 
```

cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install

```

makes problem, though the path is ok, but install not I get this error message:

```

sudo: ./install-desktop-entries.sh command not found

```

what could be the problem?

thanx in advance

---

### Post by taurus on 2006-11-05
What's the output of this command then?

```
ls -la /usr/lib/avast4workstation/share/avast/desktop
```

---

### Post by binary_dream on 2006-11-05
I get this by running that command:
```

..
..
..
-rwxr-xr-x -roor roor .............. avast.desktop
-rwxr-xr-x -roor roor .............. avast-quickscan.desktop
-rwxr-xr-x -roor roor .............. install-desktop-entries.sh

```

I've added these dots to represent some numbers, cuz I have to manually type everything from notebook on my desktop which has internet.


thanks

---

### Post by taurus on 2006-11-05
Show me the first few lines of 

```
more install-desktop-entries.sh
```

---

### Post by binary_dream on 2006-11-05
it shows some function a very long text, looks like c code or perhaps perl, but is too long I can't really type all that here, but some lines:

```

#
#this script tries to find KDE and GNOME installations and installs
#menu entries and icons for them. All actions are logged into #3unisnt.log
#


```

---

### Post by taurus on 2006-11-05
Okay, how about the first screen then?  ;)

---


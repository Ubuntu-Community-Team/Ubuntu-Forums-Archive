---
title: "Wine"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-01-10
I have wine installed but cannot install any windows application.

E.g. i am trying to install GoogleEarth. The installation screen comes up with the progress bar. It gets to one bar and does nothing else.

Not sure what I am doing wrong?

When i run:

wine h:\GoogleEarth.exe in the terminal window is says:

```
fixme:ole:ITypeInfo_fnRelease destroy child objects
```

And repeats that about 20 times - is this a problem?

---

### Post by gitfiddler on 2006-01-10
"Destroy child objects?!" Wow, does that sound nasty!

There is some interesting information about getting Google Earth to work with wine here:
[http://www.linux-tip.net/cms/content/view/215/6]("http://www.linux-tip.net/cms/content/view/215/6")

It's intended for Suse, but it may be applicable. Besides, we've got to try *something* to save those poor defenseless "child objects".

Let me know if this helps.

---

### Post by _simon_ on 2006-01-10
got a lot further and managed to install it.

But now my wine has lost drive_c and no matter how many times i add it back in it's gone each time i check.

```

simon@ubuntu:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

```

```

simon@ubuntu:~$ gEarth
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: cannot find 'home/simon/.wine/drive_c/Program'

```

---

### Post by _simon_ on 2006-01-11
managed to restore drive_c by uninstalling WINE and deleting the directory then re-installing.

Got google earth installed and running. Unfortunately there is some kind of graphics issues where google earth constantly refreshes with various bits of the menus coming and going. 

I'll have another play tonight.

---

### Post by _simon_ on 2006-01-11
don't know what i have done now but when i try and run winecfg i get this:

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  13
  Current serial number in output stream:  14

```

---

### Post by _simon_ on 2006-01-11
all sorted but google earth runs so slow that it's unusable :(

---

### Post by manicka on 2006-01-11
This may help

[http://appdb.winehq.org/appview.php?versionId=3254](http://appdb.winehq.org/appview.php?versionId=3254)

---


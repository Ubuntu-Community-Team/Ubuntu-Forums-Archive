---
title: "What does ~/ mean?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-03-13
i am attempting to follow the directions listed below and i do not understand what it means when it says "~/". also what does it mean by bump package version number?

 thanks in advance.

[I]
- Get source package : apt-get source tilda
- Install build dependencies : sudo apt-get build-dep tilda
- **Create patches dir into debian/ : for me it was ~/mybe/tilda/tilda-0.09.3/debian/patches**
- Put the patch into the patches dir named like as real_transparency.patch
- Bump package version number if you want by adding an entry to top of debian/changelog file like as tilda_0.09.3-0ubuntu1 to tilda_0.09.3-0ubuntu1.1
- From tilda-0.09.3 dir, issue build command : dpkg-buildpackage -rfakeroot
- After package built install the deb you made : sudo dpkg -i ../tilda*.deb [/I]

---

### Post by Tipo on 2007-03-13
The ~/ means your home directory :)

---

### Post by 23meg on 2007-03-13
It means the home directory of the active user. Your username being *foo*, ~/ corresponds to /home/foo.

---

### Post by enderwig on 2007-03-13
~/ is shorthand for your home directory  it is the key to the left of the 1 and above tab.  Hold shift when pressing it.

---

### Post by tribaal on 2007-03-13
Well ~/ is a shortcut to your home directory.

So for example ~/test.txt is actually /home/tribaal/test.txt on my machine :)
It's just a shortcut, to avoid typing the path to your home every time.

Hope this makes sense to you.

- trib'

---

### Post by Nuverde on 2007-03-13
~/ refers to your home directory.  (/home/username/)
similarly ~otheruser/ refers to "otheruser"s home directory.

Dont know about the Bump though.

---

### Post by jordanmthomas on 2007-03-13
bumping the version number would help to ensure that tilda was not updated by the automatic updates, ruining the patches you are applying.

---

### Post by pjones0404 on 2007-03-13
> **jordanmthomas said:**
> bumping the version number would help to ensure that tilda was not updated by the automatic updates, ruining the patches you are applying.

so how would i do this?

* Bump package version number if you want by adding an entry to top of debian/changelog file like as tilda_0.09.3-0ubuntu1 to tilda_0.09.3-0ubuntu1.1*

i appreciate all the quick responses.

:guitar:

---

### Post by jordanmthomas on 2007-03-13
I would imagine you'd go into the debian directory 
```
cd ~/mybe/tilda/tilda-0.09.3/debian/
```
...or wherever you have put your source.
Then, edit the changelog file and change the version (look for tilda_0.0.93-0ubuntu1 in the file and change it to the version you want.
```
gedit changelog
```

---


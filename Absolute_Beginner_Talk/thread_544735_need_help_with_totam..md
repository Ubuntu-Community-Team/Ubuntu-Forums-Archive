---
title: "need help with totam."
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by xxhaloownerxx on 2007-09-06
i need some help playing WMA and MP3 files, i downloaded some package that should have enabaled me to play them, but it didnt work :( (sorry for spelling/grammar errors, i cant see anything on my resolution.)

---

### Post by por100pre1 on 2007-09-06
Which package did you download? Try using this [how-to]("http://ubuntuforums.org/showthread.php?t=413624"), worked for me.

---

### Post by WebSiteGuru on 2007-09-06
Also if that dont work you can check [this one ]("http://ubuntuforums.org/showthread.php?t=524042")out

---

### Post by xxhaloownerxx on 2007-09-06
i should have noted that im using v 6.06. i do believe. and the file i installed was libmad0.

---

### Post by por100pre1 on 2007-09-06
> **xxhaloownerxx said:**
> i should have noted that im using v 6.06. i do believe. and the file i installed was libmad0.

[Here's]("https://help.ubuntu.com/community/RestrictedFormats/MP3") what you need then. :)

EDIT: Use [this]("https://help.ubuntu.com/community/RestrictedFormats") too.

---

### Post by xxhaloownerxx on 2007-09-06
> **por100pre1 said:**
> [Here's]("https://help.ubuntu.com/community/RestrictedFormats/MP3") what you need then. :)

thanks, i hate to be a noob, but exactly where would i go about finding the files it specfies in that link you gave me? thanks.

---

### Post by por100pre1 on 2007-09-06
If the guide tell you to install a package use a terminal window (Applications> Accessories> Terminal) copy paste and enter this:

```
sudo apt-get install *package-name*
```

do it for whatever packages the guide tells you.

If it tells you to remove something. Do this:

```
sudo apt-get remove *package-name*
```

If you need to enable some repositories close the terminal, reopen it, type this:

```
gksu software-properties-gtk
```

a window will appear. In it check everything except source code and close the window.

---

### Post by xxhaloownerxx on 2007-09-06
> **por100pre1 said:**
> If the guide tell you to install a package use a terminal window (Applications> Accessories> Terminal) copy paste and enter this:

```
sudo apt-get install *package-name*
```

do it for whatever packages the guide tells you.

If it tells you to remove something. Do this:

```
sudo apt-get remove *package-name*
```

If you need to enable some repositories close the terminal, reopen it, type this:

```
gksu software-properties-gtk
```

a window will appear. In it check everything except source code and close the window.

i tried the 1st one and i got this error

Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.10-plugins-ugly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-plugins-ugly has no installation candidate

---

### Post by WebSiteGuru on 2007-09-06
Have you enable all software sources in Sympatic?

---

### Post by xxhaloownerxx on 2007-09-06
> **WebSiteGuru said:**
> Have you enable all software sources in Sympatic?

not sure what you mean by that.

---


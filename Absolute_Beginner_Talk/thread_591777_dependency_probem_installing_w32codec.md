---
title: "dependency probem installing w32codec"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by arKin on 2007-10-25
hi im having troubles installing w32codec.  when i go to install it i get the error

 w32codecs: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
 
so i went: sudo apt-get install libstdc++5

and got: Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate

im running gutsy and im extremely new to ubuntu so this is probably just some rookie mistake. 
any help would be much appreciated.  thanks in advance

---

### Post by overdrank on 2007-10-25
> **arKin said:**
> hi im having troubles installing w32codec.  when i go to install it i get the error

 w32codecs: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
 
so i went: sudo apt-get install libstdc++5

and got: Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate

im running gutsy and im extremely new to ubuntu so this is probably just some rookie mistake. 
any help would be much appreciated.  thanks in advance

Hi maybe these links will help
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Good luck!

---

### Post by Maestro23 on 2007-10-25
> **arKin said:**
> hi im having troubles installing w32codec.  when i go to install it i get the error

 w32codecs: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
 
so i went: sudo apt-get install libstdc++5

and got: Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate

im running gutsy and im extremely new to ubuntu so this is probably just some rookie mistake. 
any help would be much appreciated.  thanks in advance

Make sure your Universe and Multiverse Repo's are enabled.

System>>Admin>>Software Resources

Then try again.

---


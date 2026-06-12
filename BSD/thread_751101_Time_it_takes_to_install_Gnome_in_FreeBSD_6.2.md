---
title: "Time it takes to install Gnome in FreeBSD 6.2"
date: 2008-04-10
forum: BSD
---

### Post by munkyeetr on 2008-04-10
I have FreeBSD 6.2 installed on a virtual machine (vmware). I decided to try installing gnome last night, and did the following:
```

# cd /usr/ports/x11/gnome2
# make clean
# make install clean

```
it then began (what looked like) compiling every piece of the gnome desktop from source.

Anyway, that was last night...I got up this morning and it was still compiling **9 hours later**.

Is it normal to take this long?

---

### Post by D-EJ915 on 2008-04-11
yes, it takes forever to compile the desktop environments, and other things like open office which takes forever x2

---

### Post by munkyeetr on 2008-04-11
well, at least I know it's not a screw up...thanx

---

### Post by phoqueyoo on 2008-04-12
You must have a slow CPU. Why don't you just use the binaries?

---

### Post by ibutho on 2008-04-12
For an initial install, I usually use the prebuilt packages which can be installed by doing 
```
#pkg_add -r gnome2
```
You can then use ports to update and refine the package options at a later stage.

---

### Post by munkyeetr on 2008-04-12
> **phoqueyoo said:**
> You must have a slow CPU. Why don't you just use the binaries?

Yes I do have a slow CPU, thank you.

> **ibutho said:**
> For an initial install, I usually use the prebuilt packages which can be installed by doing 
```
#pkg_add -r gnome2
```
You can then use ports to update and refine the package options at a later stage.

I will try that.

---


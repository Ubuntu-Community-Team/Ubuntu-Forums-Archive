---
title: "Is it possible to build packages from source with aptitude?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-02-12
```

  $ apt-get update
  $ apt-get source mypackage
  $ cd mypackage_1.1.5

```

Modify source and rebuild deb package with

```

  $ fakeroot dpkg-buildpackage -b -uc -us
  $ cd ..
  $ dpkg --install mypackage_1.1.5-1_i386.deb

```

Can all these be accomplished with aptitude instead?

Thanks!

---

### Post by Kyral on 2006-02-13
[quote=Akhran]```

  $ apt-get update
  $ apt-get source mypackage
  $ cd mypackage_1.1.5

``` 
Modify source and rebuild deb package with

```

  $ fakeroot dpkg-buildpackage -b -uc -us
  $ cd ..
  $ dpkg --install mypackage_1.1.5-1_i386.deb

``` 
Can all these be accomplished with aptitude instead?

Thanks![/quote]

Well, if you have to mod the source, then you have to stop the process in between. But to pull and build in one move, do this

```
sudo apt-get build-dep <package>
```
This isn't the command to build, rather it makes sure that you have everything you need to build it

Then
```
sudo apt-get source -b <package>
```
This will download and build. You'll still need to use dpkg -i to install it however

---


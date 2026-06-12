---
title: "monodevelop installation for beginner"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by mistermc on 2008-02-29
I am trying to setup Ubuntu 6 LTS as a web server for .net appliactions.
When trying to run the install command:
sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop monodoc-browser monodevelop-nunit monodevelop-versioncontrol

I get the error:

Couldn't fimd the package MONODEVELOP.

I am assuming that this is because the package isn't installed. How do I install?

---

### Post by SOULRiDER on 2008-02-29
The problems is that there is no such package for Dapper. Im not running dapper so I cant help you much. Someone who runs dapper and monodevelop should post here and guide you.

---

### Post by SOULRiDER on 2008-02-29
It seems i amde a mistake, monodevelop seems to be in the universe repo.
[http://packages.ubuntu.com/dapper/monodevelop](http://packages.ubuntu.com/dapper/monodevelop)

Make sure you ahve Universe enabled.

---

### Post by igknighted on 2008-02-29
Use a newer version of Ubuntu... yes, packages exist for Dapper.  But they are two years old now.  You should use 7.10 (or soon 8.04) to make sure you are as .NET compatible as possible.

---

### Post by SOULRiDER on 2008-02-29
> **igknighted said:**
> Use a newer version of Ubuntu... yes, packages exist for Dapper.  But they are two years old now.  You should use 7.10 (or soon 8.04) to make sure you are as .NET compatible as possible.

I would wait until 8.04 to be honestsince its the next LTS release, and actually a week or two after its out, since theres always a sneaky bug waiting to happen.

---


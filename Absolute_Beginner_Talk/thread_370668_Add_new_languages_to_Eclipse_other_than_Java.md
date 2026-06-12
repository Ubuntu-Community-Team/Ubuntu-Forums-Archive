---
title: "Add new languages to Eclipse other than Java"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-26
I have been told that Eclipse can compile C and C++ and possibly other languages. I am mostly used to Visual Studio and have never really used Eclipse. I would greatly appreciate if you could tell me the steps so that I can add additional languages to Eclipse and be able to compile in those languages. 

Thanks

:popcorn:

---

### Post by pirothezero on 2007-02-26
You need to use the CDT plugin, its on something like [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/).

You may need subversion, I currently do not have CDT installed on my eclipse build.

---

### Post by phossal on 2007-02-26
Depending on how you installed eclipse, you can download the plugin .tar.gz, extract it, and then copy the contents of both its features and plugins folders into those of the same name within your eclipse directory. After that, restarting eclipse makes the plugins available.

---

### Post by konst88 on 2007-02-26
Just:
sudo aptitude install eclipse-cdt

---

### Post by phossal on 2007-02-26
The potential problem with that is that the versions are out of sync. CDT versions are tightly related to those of eclipse. So, if you're using packages, you're either stuck being out of date, or you have to do it manually, or you risk performance problems. Packages are great. Use them if you want, but consider all the info, at least.

---


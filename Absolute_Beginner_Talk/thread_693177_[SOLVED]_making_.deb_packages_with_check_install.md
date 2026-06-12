---
title: "[SOLVED] making .deb packages with check install"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2008-02-10
Hi I'm fairly new to compiling things from source

 I compiled the latest version of wine, applying an alpha glow patch and using checkinstall to make a .deb package.

Compiling wine takes a long time, if I formatted and reinstalled, could I just use the .deb package I made with checkinstall to reinstall it?

And also, if I distributed this package to other users, would they be able to use it as well?

Thanks

---

### Post by spiderbatdad on 2008-02-10
[http://www.gnu.org/licenses/](http://www.gnu.org/licenses/) I believe you should provide documentation with your package and point to package sources and libraries.

---

### Post by SunnyRabbiera on 2008-02-10
well why compile?
most of the best stuff is already on the repos...

---

### Post by piratesmack on 2008-02-10
The newest version of wine just came out a few days ago. There is only the source code, no prebuilt binaries yet

Plus I have to compile so I can apply the 3dmark patch required to play games like call of duty 4 in wine

---

### Post by Majorix on 2008-02-10
You can use their repo for the latest .deb, pre-compiled.

---

### Post by piratesmack on 2008-02-10
> Binary packages are in the process of being built and it may take a few days for them to appear, but the source is available now. You can find out more about this release in the announcement. Check out our download page for packages for your distribution.

Plus like I said I have to apply a patch to the source to get call of duty 4 running

---

### Post by piratesmack on 2008-02-10
Basically what I'm asking is what's the best way to make a debian package. Is checkinstall good enough? At least for installing on the computer I compiled it on

---

### Post by Majorix on 2008-02-10
> **spiderbatdad said:**
> [http://www.gnu.org/licenses/](http://www.gnu.org/licenses/) I believe you should provide documentation with your package and point to package sources and libraries.

That's not necessarily right, I remember I have built a .deb package without pointing to anything, but I don't remember how I did it :(

---

### Post by piratesmack on 2008-02-10
> **spiderbatdad said:**
> [http://www.gnu.org/licenses/](http://www.gnu.org/licenses/) I believe you should provide documentation with your package and point to package sources and libraries.

OK I will, but is using checkinstall good enough? Will it work right on other computers?

---

### Post by PeterJS on 2008-02-10
Checkinstall should be good enough for personal use, but not so good for distribing. The reason they're no good for distributing is that the step to configure what dependacies the package needs and provides is optional and most people (I know I do) skip it, further more from looking at it, it looks pretty cryptic and I'm not sure how easy it would be set up even if you wanted to.

Specifically to the question of installing it on other machines, it should be do able as long as they are the same arch, ie no going from x86 to amd64 and vice versa. But like I said, dependencies for checkinstall packages are hit or miss, so you'll have to do it by hand if it's anything above and beyond the base install.

---

### Post by piratesmack on 2008-02-10
> **PeterJS said:**
> Checkinstall should be good enough for personal use, but not so good for distribing. The reason they're no good for distributing is that the step to configure what dependacies the package needs and provides is optional and most people (I know I do) skip it, further more from looking at it, it looks pretty cryptic and I'm not sure how easy it would be set up even if you wanted to.

Alright thanks man :)

---


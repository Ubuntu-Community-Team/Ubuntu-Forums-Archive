---
title: "Installation size of firefox"
date: 2009-02-08
forum: Arch and derivatives
---

### Post by benerivo on 2009-02-08
When i install firefox, it brings in xulrunner, which requires 70MB+ of disk space. Why is xulrunner needed, as i can download firefox from the mozilla website (10MB) and run it from the extracted tarball? I don't really need an answer, but i'm interested as to why this is the case.

---

### Post by fwojciec on 2009-02-09
It's basically the package maintainer's choice.  I suppose it makes sense from his perspective, since he would have to build xulrunner anyways as other packages (like epiphany) require it.  Xulrunner, I think, contains much of what makes firefox work and also some mozilla development stuff, so it's a big package.

I build my own version of firefox without the xulrunner dependency, which means that parts of xulrunner (without the dev stuff) are built directly into firefox -- personally I prefer it this way, although the point is not to save disk space (I have xulrunner installed anyways since I use epiphany as my backup browser so I end up using more disk space, in fact) but to build firefox with profiling enabled so it is optimized for my system for slightly better performance.  My firefox package takes up about 26MB of disk space when installed.

If you're interested there should be some firefox PKGBUILDS in AUR that also require xulrunner, I think.

---

### Post by kerry_s on 2009-02-09
> **benerivo said:**
> When i install firefox, it brings in xulrunner, which requires 70MB+ of disk space. Why is xulrunner needed, as i can download firefox from the mozilla website (10MB) and run it from the extracted tarball? I don't really need an answer, but i'm interested as to why this is the case.

it's built to take advantage of the system, you'll find the 1 from the mozilla site is way slower in startup, display, etc...

---

### Post by namegame on 2009-02-09
You could also search for the swiftweasel packages in the AUR. Swiftweasel is supposed to be Firefox optimized for different architectures. Personally, I didn't notice a huge difference, but your mileage may vary.

---

### Post by smartboyathome on 2009-02-09
> **namegame said:**
> You could also search for the swiftweasel packages in the AUR. Swiftweasel is supposed to be Firefox optimized for different architectures. Personally, I didn't notice a huge difference, but your mileage may vary.

There is even firefox-pgo in AUR which takes a long time to compile, but then is xulrunner independant.

---


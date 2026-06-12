---
title: "[SOLVED] Firefox3 in Arch - Rebuilt for i686 or official build?"
date: 2008-06-23
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-06-23
Is the firefox3 package in Arch recompiled using i686 flags or does it use the official mozilla build?

---

### Post by crimesaucer on 2008-06-23
I could be wrong, but when I download the Minefield nightly, it said i686: [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

but, I'm not sure if it is different than the actual final release.

---

### Post by handy on 2008-06-23
I just did an -Syu during which my Firefox was updated with the firefox-3.0-1_x86_64 which is described in the following words in the Arch Extras repo':

 	***Standalone web browser from mozilla.org***

---

### Post by kpkeerthi on 2008-06-24
[http://repos.archlinux.org/viewvc.cgi/firefox/repos/extra-i686/PKGBUILD?revision=3300&view=markup](http://repos.archlinux.org/viewvc.cgi/firefox/repos/extra-i686/PKGBUILD?revision=3300&view=markup)

Arch does not use the official mozilla 'binary'. The package is rebuilt - note that **make** is run in PKGBUILD. So it is i686/x86_64 optimized.

---

### Post by MisfitI38 on 2008-06-24
> **kpkeerthi said:**
> [http://repos.archlinux.org/viewvc.cgi/firefox/repos/extra-i686/PKGBUILD?revision=3300&view=markup](http://repos.archlinux.org/viewvc.cgi/firefox/repos/extra-i686/PKGBUILD?revision=3300&view=markup)

Arch does not use the official mozilla 'binary'. The package is rebuilt - note that **make** is run in PKGBUILD. So it is i686/x86_64 optimized.

That's part of the reason why the program is called 'Minefield', (formerly Bon Echo for v2.x). It is not the 'official' branded Firefox. :)

---

### Post by handy on 2008-06-25
@*** MisfitI38***:

Man you have got such a great avatar.

Well done... :KS

---


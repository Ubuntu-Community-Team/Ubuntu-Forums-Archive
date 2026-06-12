---
title: "Installing NetBSD on a sparc64"
date: 2007-08-07
forum: BSD
---

### Post by Nikron on 2007-08-07
Well, after I couldn't get my sun keyboard type 5c to work in FreeBSD, I switched to NetBSD.  So, far it's been great except for the fact that NetBSD still uses Xfree86, instead of xorg.  Oh well..  The keyboard works =P.  I'm doing this on a Sun Ultra 5.

So, far the NetBSD experience is great, except compiling for source takes a while.  Maybe I should switch to binary.  Anyone else actively use NetBSD as a desktop?  Preferably on weird hardware?

---

### Post by angryfirelord on 2007-08-20
NetBSD runs on may architectures, so it takes a while for things to catch up.

I know in FreeBSD, you can just do pkg_add -r <name_of_package> and it will update, but I'm not sure for NetBSD.

---

### Post by -Rick- on 2007-08-21
> **Nikron said:**
> Well, after I couldn't get my sun keyboard type 5c to work in FreeBSD, I switched to NetBSD.  So, far it's been great except for the fact that NetBSD still uses Xfree86, instead of xorg.  Oh well..  The keyboard works =P.  I'm doing this on a Sun Ultra 5.

So, far the NetBSD experience is great, except compiling for source takes a while.  Maybe I should switch to binary.  Anyone else actively use NetBSD as a desktop?  Preferably on weird hardware?

I have NetBSD installed on my regular PC, with kde and everything (though hardly use it these days).

NetBSD is migrating X.org in the base system afaik. In the meanwhile you can install X.org from pkgsrc however.

---


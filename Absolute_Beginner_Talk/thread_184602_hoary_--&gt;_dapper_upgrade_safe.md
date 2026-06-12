---
title: "hoary --&gt; dapper upgrade safe?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by roots on 2006-05-30
hi there,

i never did it before, so to avoid wrecking my laptop ubuntu installation, i'd like to know if it is safe to upgrade from hoary to dapper (rc) or if it is wiser to do a complete clean new install? are there any cons or restrictions?

would ```
apt-get dist-upgrade -d
``` be right the thing to do?


cheers,
roots

---

### Post by Sef on 2006-05-30
No it is not safe.  Do a clean install.  Otherwise your system will break.

---

### Post by meborc on 2006-05-30
i could not agree more... upgrade from breezy is sometimes a pain... from hoary...  there are so many new things... i guess you could not make out of it...

---

### Post by [S|G] on 2006-05-30
Depends on what you call safe. I upgraded from breezy to dapper using dist-upgrade and had to fix some problems later (re-install openoffice and amarok).

If you don't want to end up with some missing programs you shouldn't dist-upgrade. If you're willing to reinstall the packages it shouldn't be a problem though.

---

### Post by Gustav on 2006-05-30
Breezy->Dapper is meant to work but Hoary->Dapper will probably not.

If you absolutely want to upgrade then first upgrade to Breezy, then Dapper.

---


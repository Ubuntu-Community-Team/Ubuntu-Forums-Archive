---
title: "Can I install a Dapper package in Breezy?"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by outofsync on 2006-03-29
I need the _real_ Korn shell (ie: not pdksh because it doesn't work with my old scripts).

I see that it's available on Dapper only.

Can I install it on Breezy?

Thanks

---

### Post by mostwanted on 2006-03-29
Probably not.

If it's not been backported it's either because it has depencies on newer libraries or no one's asked.

[http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)

---

### Post by tomski on 2006-03-29
you can install dapper .debs but it may break other packages that are installed so it may be better to try to install the src package instead

---

### Post by outofsync on 2006-03-29
I found it as a Debian package whose libc dependencies seem to be met by Breezy. It just installs an executable in /usr/bin, a file in /usr/lib/menu, as well as a manpage and various docs.

Do you believe it would be safe to install such Debian package?

---

### Post by meborc on 2006-03-29
well.. it is safe to try... you can always 'remove' it later... if it doesn't work

---

### Post by cronholio on 2006-03-29
I do that all the time. You might have to remove it before an upgrade though.

---


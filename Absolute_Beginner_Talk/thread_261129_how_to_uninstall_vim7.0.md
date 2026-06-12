---
title: "how to uninstall vim7.0?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-09-19
i downloaded the vim7.0 tar and ran make install. now i want to uninstall it. anyone know how to do this?

Thanks

---

### Post by croak77 on 2006-09-19
Do you still have the folder where you typed sudo make install? If you do cd to that folder and run sudo make uninstall.

---

### Post by jinxjinx on 2006-09-20
thanks!

---

### Post by colo on 2006-09-20
Don't EVER install software that's in your distribution's repositories from source. Honestly - Just don't (unless you desperately need another version that's not in your repos), OK? ;)

---

### Post by skymt on 2006-09-20
> **colo said:**
> Don't EVER install software that's in your distribution's repositories from source. Honestly - Just don't (unless you desperately need another version that's not in your repos), OK? ;)

Vim 7 isn't in Dapper, and it has great new features like Intellisense-style completion and spell checking. For large updates like this, it makes sense to compile from source.

---


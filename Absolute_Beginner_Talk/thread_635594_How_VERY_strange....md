---
title: "How VERY strange..."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by collierd45 on 2007-12-08
If you look at the attached screenshot, anything in my home directory appears on the desktop for some reason.

Any ideas?

---

### Post by sloggerkhan on 2007-12-08
that's odd.

---

### Post by collierd45 on 2007-12-08
> **sloggerkhan said:**
> that's odd.

Certainly is, any ideas?

---

### Post by Teknyk on 2007-12-08
Under the configuration editor > apps > nautilus > preferences...
Is "desktop_is_home_directory" checked possibly?

---

### Post by collierd45 on 2007-12-08
> **Teknyk said:**
> Under the configuration editor > apps > nautilus > preferences...
Is "desktop_is_home_directory" checked possibly?

Nope, it's unchecked :/

---

### Post by collierd45 on 2007-12-08
It's wierd, if I click 'Desktop' in the places menu it goes straight to my home dir, rather than to the desktop folder in my home dir :/

---

### Post by WearZeeP on 2007-12-08
Check ~/.config/user-dirs.dirs, look at the the variable "XDG_DESKTOP_DIR", what does it say?

---

### Post by collierd45 on 2007-12-08
"XDG_DESKTOP_DIR="$HOME/"

Im assuming it should be $home/desktop?

Thanks

---

### Post by collierd45 on 2007-12-08
Changed it and all's good.

I love you more than my mother... well, almost haha

---

### Post by WearZeeP on 2007-12-08
> **collierd45 said:**
> Changed it and all's good.

I love you more than my mother... well, almost haha


Haha, well, no probem at all!
Just fun to help out.

---


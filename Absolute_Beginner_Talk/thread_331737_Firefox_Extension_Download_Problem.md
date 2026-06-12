---
title: "Firefox Extension Download Problem"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Jaybird on 2007-01-05
When I try to download an extention for Firefox, I get a message that says "Software installation is currently disabled.  Click edit options...enable it and try again."  When I do that, I can't see where to enable anything.  ?

---

### Post by 23meg on 2007-01-05
What version of Firefox and Ubuntu are you using? Did you install or upgrade Firefox yourself?

---

### Post by Jaybird on 2007-01-05
Firefox is 1.5.0.9 that Ubuntu upgrade just yesterday.  Ubuntu 6.06.

---

### Post by Jaybird on 2007-01-05
Here's something, but I don't know how to fix it.  When I start Firefox with sudo, I'm allowed to download the extensions, but not when I'm logged in as a user.  Anyone know how to change that?

---

### Post by 23meg on 2007-01-05
Make sure you have write access to your Firefox profile directory, which is under ~/.mozilla/firefox .

---

### Post by Jaybird on 2007-01-05
I do, but still no luck.

---

### Post by Jaybird on 2007-01-05
Found the solution here:
[http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_-_Firefox](http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_-_Firefox)

---


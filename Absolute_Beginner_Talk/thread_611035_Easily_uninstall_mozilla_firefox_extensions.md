---
title: "Easily uninstall mozilla firefox extensions?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by ntu on 2007-11-12
Can you easily uninstall mozilla firefox extensions? And if so, how?

I have not installed any as yet, but want to make sure that I can completely uninstall before I try.

With best wishes,

---

### Post by reckless2k2 on 2007-11-12
well you can remove them from the add/remove menu. you can't remove them in firefox like normal extensions. i had some problems using add/remove. i'd suggest traditional install through firefox as opposed to in add/remove ubuntu menu.

---

### Post by por100pre1 on 2007-11-12
> **ntu said:**
> Can you easily uninstall mozilla firefox extensions? And if so, how?

I have not installed any as yet, but want to make sure that I can completely uninstall before I try.

With best wishes,

Create a new profile and they will be gone:

```
firefox -ProfileManager
```

---

### Post by finer recliner on 2007-11-12
in firefox, when you go to tools > addons, it brings up a list of all extenstions you have installed. each extension has a 'preferences', 'disable' and 'uninstall' button associated with it. very easy and very convenient.

---

### Post by KhaaL on 2007-11-12
The hardcore user might be intrested that uninstalling addons sometimes leaves leftovers in the file: /home/$USER/.mozilla/firefox/[your profile].default/prefs.js

Only way I know of  to clean it up is manually, so fire up your favorite text editor!

---

### Post by ntu on 2007-11-12
Thank you very much for all your responses. I feel more confident to tackle ff extensions now.

---


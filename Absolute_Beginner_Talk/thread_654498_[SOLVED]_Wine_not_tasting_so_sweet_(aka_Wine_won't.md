---
title: "[SOLVED] Wine not tasting so sweet (aka Wine won't open)"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by juniah on 2007-12-31
no matter what I do in Wine....

```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x5b
  Serial number of failed request:  13
  Current serial number in output stream:  15

```

has my wine been 'corked'?

Note:
Thats a bad pun.  Winos and the like will know that when wine (of the drinking persuasion) when a wine is 'corked' it means that a piece of the cork has fallen into the wine rotten and spoiled the w

---

### Post by foolsh on 2007-12-31
are you using the latest release .9.52?
did you run winecfg?

---

### Post by juniah on 2007-12-31
winecfg won't run I get the same error.

no I'm not running that version, but i will be shortly.

UPDATE:

No go.  Same error as before.  Not even winecfg is fixed.  Wine just isn't working :(

---

### Post by argie on 2007-12-31
Was it working before? If so try starting afresh:
```

mv ~/.wine ~/.wine.backup

```

---

### Post by juniah on 2007-12-31
Thank you!  wine is working once again.

---


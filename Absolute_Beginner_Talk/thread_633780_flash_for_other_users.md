---
title: "flash for other users"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by jkrumm on 2007-12-06
I managed to install flash on my laptop, but after I set up my daughter as a user when she logs on Firefox doesn't have flash installed. Is there an easy way to fix it besides re-installing it for her desktop?

---

### Post by misfitpierce on 2007-12-06
perhaps copy the firefox folder from your profile and root into hers? if not perhaps just reinstall flash plugin lol.

(oh how I hope flash auto installer is fixed soon)

---

### Post by delphiguy on 2007-12-06
you might want to check this thread.
[http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)

hope this helps.

---

### Post by pointfivezero on 2007-12-06
> **jkrumm said:**
> I managed to install flash on my laptop, but after I set up my daughter as a user when she logs on Firefox doesn't have flash installed. Is there an easy way to fix it besides re-installing it for her desktop?

As an interim solution you could copy you local flash plugin to the flashplugin-nonfree installation directory, which should make it work for all users.

```

sudo cp ~/.mozilla/plugins/libflashplugin.so /usr/lib/flashplugin-nonfree/

```

Replace cp with mv to move it and save any niggles once the flashplugin-nonfree is updated...

---


---
title: "Synaptic error"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by degro on 2007-09-11
Hey guys.

I have this problem. I tried to install Maya 8.5 on my Ubuntu feisty machine, but for some reasons it failed. When I got into synaptic and wanted to uninstall it if any files were installed, I got this nasty error:

> E: The package maya8-0-64 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Could somebody please help me? I want my synaptic back :(

Thanks a lot.

---

### Post by degro on 2007-09-11
great... seems like my system's ft up. i guess i'll just reinstall it. or go for opensuse.

---

### Post by ambush_xx on 2007-09-11
sudo dpkg --force-remove-reinstreq --remove maya8-0-64

---

### Post by degro on 2007-09-11
i think i love you.
it worked.

thanks a lot mate!

---


---
title: "Searching as R00T (Solved)"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-02
Hey all! :)

Hope everyone is **doing** **well** everywhere.

I **recently** uninstalled eclipse java editor because it was not working properly. I **removed** it using the **synaptic** package manager but, being an recently converted windows user lol, i went to Places --> Search for Files... "Eclipse" and like 19 files where found, but when i selected them all and selected move to trash, it said **access denied**?

Do i have to do this **every time** i delete an app like Eclipse w/ multiple plugins and packages?

Do i physically have to go to **every** folder and delete stuff?

**or** can I run Search for Files... as root? if so how?

What would prevent this in the future(all the left over garbage)?

---

### Post by aysiu on 2005-12-02
You can try Alt-F2 ```
gksudo gnome-search-tool
``` By the way, you should never need to manually delete packages after uninstalling them. See screenshots for two options you may like: mark for complete removal and delete cached package files.

---

### Post by adduds on 2005-12-02
thank you very much my friend! :) it worked aside from a couple folders. And I did mark for complete removal but I installed eclipse from outside synaptic (tar.gz) file so i think that was the one which was lingering around...I'm not entirely sure if that's the reason. but thanks :)

cheers,
ad

---


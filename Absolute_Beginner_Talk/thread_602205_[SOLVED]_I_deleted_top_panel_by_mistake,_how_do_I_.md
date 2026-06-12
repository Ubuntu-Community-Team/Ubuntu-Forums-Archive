---
title: "[SOLVED] I deleted top panel by mistake, how do I get it back pl"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Cool Surfer on 2007-11-04
I deleted top panel by mistake, how do I get it back pl

---

### Post by Fred_E _krugar on 2007-11-04
Just right click at the top and add new panel

---

### Post by aysiu on 2007-11-04
> **Fred_E _krugar said:**
> Just right click at the top and add new panel
Or you may have to right-click on the bottom panel and select *New Panel*

---

### Post by Fred_E _krugar on 2007-11-04
ok sorry I stand corrected

---

### Post by Cool Surfer on 2007-11-04
ok an empty panel is created.

I cant see the minimised windows. how do I bring thm there when they are minimised?

---

### Post by American_Outcast on 2007-11-04
> **Cool Surfer said:**
> ok an empty panel is created.

I cant see the minimised windows. how do I bring thm there when they are minimised?


Right click the new empty panel you just created and click on " add to panel " Then add " Window List " Which is under the Desktop & Windows section.

---

### Post by aysiu on 2007-11-04
If you want the default panel items back, you can paste this command into the terminal: ```
mv ~/.gconf/apps/panel ~/.gconf/apps/panel.old
``` You may have to log out for the change to take effect.

---

### Post by Cool Surfer on 2007-11-04
Thanks friends, I just added wiindows list to the bottm panel, so dont need the top one :)
Great help!! Cheers!!:guitar:

---

### Post by Incense on 2007-11-04
If you want to get your panels back to the default out of the box look, type the following into a term. 

```
rm -r ~/.gconf/apps/panel
```

Then log out and when you log back in your panels will be restored.

EDIT: aysui already beat me, I need to read a bit more closely next time...

---


---
title: "Desktop Effects menu gone"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by richardgundersen on 2007-07-28
Hi

Please could someone tell me how to reinstall Desktop Effects. The menu has gone from System -> Preferences. 

It's probably because I uninstalled Beryl while I was trying out Compiz Fusion. But now I want it back to the original setting!

Thanks

---

### Post by overdrank on 2007-07-28
> **richardgundersen said:**
> Hi

Please could someone tell me how to reinstall Desktop Effects. The menu has gone from System -> Preferences. 

It's probably because I uninstalled Beryl while I was trying out Compiz Fusion. But now I want it back to the original setting!

Thanks

HI, this  is the first command in the "how to"
```
sudo apt-get remove compiz-core desktop-effects
```

So I would just replace the remove with  "install" and that should get you going. Hope this helps good luck! :)

---

### Post by por100pre1 on 2007-07-28
Remove the repos you added to install compiz fusion , if any.  Then:

```
sudo apt-get install beryl beryl-manager compiz emerald desktop-efects
```

Hope this helps.

EDIT: Didn't see your post Overdrank...

---

### Post by richardgundersen on 2007-07-28
That worked perfectly - thanks!

---


---
title: "Major Problem"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-10-08
[http://img206.imageshack.us/img206/5753/screenshotsp7.png](http://img206.imageshack.us/img206/5753/screenshotsp7.png)

I'm not exactly sure what happened. All I did was install a few programs from "Add/Remove"...

I type that into Terminal and some odd menu comes up that has an okay button that I can't click.

---

### Post by overdrank on 2007-10-08
> **Cheese Roller said:**
> [http://img206.imageshack.us/img206/5753/screenshotsp7.png](http://img206.imageshack.us/img206/5753/screenshotsp7.png)

I'm not exactly sure what happened. All I did was install a few programs from "Add/Remove"...

I type that into Terminal and some odd menu comes up that has an okay button that I can't click.

Ok just do that 
```
sudo apt-get install -f
```

---

### Post by Cheese Roller on 2007-10-08
Didn't you read my post?

---

### Post by JBAlaska on 2007-10-08
Did you try running synaptic

---

### Post by Cheese Roller on 2007-10-08
Yes. I  click "Fix Broken Packages" and nothing happens.

---

### Post by JBAlaska on 2007-10-08
You need to uninstall the bad packages in synaptic. Your going to need to know which packages to uninstall

Hopefully when you do a "sudo apt-get install -f" you can read which packages need uninstalling.

---


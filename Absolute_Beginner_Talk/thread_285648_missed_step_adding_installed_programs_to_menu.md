---
title: "missed step adding installed programs to menu?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by dief-eh? on 2006-10-27
hello
synaptic tells me there are 1596 installed programs on this up-to-date dapper. but many don't appear in any of the applications listed on the drop down menu. how do i make them show up?

apologies if this is way below basic; i searched this forum but didn't get any results.

thanks in advance.

---

### Post by IYY on 2006-10-27
Not every package is an application you as a user would want to use (some aren't applications at all, but libraries and such). Some are not graphical, so it's not logical to have them in a graphical menu. However, your menu does not show you even all graphical applications installed. To enable that, you'll need to enable the Debian menu.

```
sudo apt-get install menu-xdg
```

---

### Post by dief-eh? on 2006-10-27
thanks so much for your reply! that helps a lot.

---


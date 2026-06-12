---
title: "Firefox won't start!!!!!!!!!!!!!!!!!"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2006-12-23
After logging in my account, firefox, for some reason, won't start!

I uninstalled and installed it already but it still won't start!

What can I do?

---

### Post by dutchmega on 2006-12-23
You can use less "!"
Are you using Dapper or Edgy?

Try:
sudo apt-get remove firefox --purge
rm -r ~/.mozilla
sudo apt-get install firefox

---

### Post by wersdaluv on 2006-12-23
Sorry for the exclamation points. I was too carried away..

I'm using edgy

---

### Post by bulldog on 2006-12-23
Using Edgy is no excuse.................:D :D 

You can try to go to your /home and rename your .mozilla so firefox will create a new profile.
This will be a clean one without your bookmarks and extensions,you have to copy them later.

---


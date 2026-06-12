---
title: "[SOLVED] Where are the cookies for Firefox located?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-15
Hi,

I tried searching for cookies as wget needs them.....where are they located? i can't find them...

:confused:

---

### Post by wolfen69 on 2007-08-15
wow!

---

### Post by aysiu on 2007-08-15
~/.mozilla/firefox/*profile name*/cookies.txt

But the file says this at the top: ```
# This is a generated file!  Do not edit.
# To delete cookies, use the Cookie Manager.
```

---

### Post by wolfen69 on 2007-08-15
am i missing something? ...ok

---

### Post by Hopeless on 2007-08-15
so..

wget --mirror --load-cookies ~/.mozilla/firefox/profile name/cookies.txt [www.somewhere.com](www.somewhere.com)

is that right?

---

### Post by zdux0012 on 2007-12-27
man wget

wget is pretty amazing
There is mechanize for ruby/php when you reach the limitation. mechanize acts as a javascriptless browser. You can click the first link in the third table.

---


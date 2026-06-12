---
title: "the content of websites"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-10-12
Is there any specific folder for that? if i have loaded it.

---

### Post by po0f on 2006-10-12
Somenoob,

Do you mean to say you have installed a web server and are looking for where it puts the html files?  Try /var/www.

---

### Post by Somenoob on 2006-10-12
> **po0f said:**
> Somenoob,

Do you mean to say you have installed a web server and are looking for where it puts the html files?  Try /var/www.

Not at all, i'm talking about when you load a site with your own web broswer, where does the contents of the page go?

---

### Post by po0f on 2006-10-12
Somenoob,

What you're referrring to is a browser's *cache*.  It depends on what browser you're using.  If it's Firefox, it's located at ~/.mozilla/firefox/*/Cache/.  After a quick glance, I don't think what's saved there is what you want.

If you want to look at a web page's source (the HTML), in Firefox just press Ctrl-U.

---

### Post by Somenoob on 2006-10-12
thanks that's what i needed to know.

---

### Post by xpod on 2006-10-12
Type "about:cache" in your Firefox address bar and it will give you all your cached pages

---


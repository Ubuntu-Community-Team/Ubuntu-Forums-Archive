---
title: "Apache network file"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by godsfshrmn on 2007-10-07
I made a mistake in webdmin with an IP address and apache will not restart. Where can I find the config file so I can manually remove it? I did not see it in the file /etc/apache2/apache2.conf
It was the 'listen on network addresses and ports' setting.

---

### Post by kidders on 2007-10-09
Hi there,

Try **grep -lir "whatever" *** from /etc to see if you can find the text you're looking for. When searching for an IP address, bear in mind that '.' has a special meaning for many apps, including grep, so you might need to search for something like "12\.34\.56\.78" to get accurate results (ie escape the dots).

---


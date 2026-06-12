---
title: "Apache Standard Practice"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by psylance on 2008-03-01
Where do you guys put ur website assuming u have a large website?

by default it's /var/www/apache2-default

---

### Post by jmagsho on 2008-03-01
I think that's strictly a matter of preference.  If it were me, I would put it on a separate drive and change the webroot in the httpd.conf folder to direct it there.    Not only will this result with a cleaner install from an administrative point, it gives you a slight security increase too since you are no longer using the defaults (IMHO, at least).

---


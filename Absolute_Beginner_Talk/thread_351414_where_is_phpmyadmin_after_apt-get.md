---
title: "where is phpmyadmin after apt-get?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by braddcadd on 2007-02-01
I installed phpmyadmin with aptitude but nothing was added to /var/www (localhost).  Should I direct the browser somewhere else or do I need to do some configuration?

---

### Post by braddcadd on 2007-02-01
looks like it is installed in /usr/share/phpmyadmin

i did the following and it worked:
```

sudo mkdir /var/www/phpmyadmin
sudo cp -R /usr/share/phpmyadmin/* /var/www/phpmyadmin/

```

although maybe I should have used a link or something.  hope this helps someone out there.

---


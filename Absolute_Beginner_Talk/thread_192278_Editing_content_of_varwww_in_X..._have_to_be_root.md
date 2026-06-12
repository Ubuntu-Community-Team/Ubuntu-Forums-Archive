---
title: "Editing content of /var/www in X... have to be root?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by otis_u on 2006-06-08
Hi. I've spent a some time in other ubuntu distributions and ended up creating myself a root login- according to popular opinion this isn't the best thing to do, so I'm trying to avoid it.

I'm running an Apache2 server and am getting upset at the fact that I can't simply drag and drop my files into /var/www inside GNU... It seems kind of ridiculous that I would need to use console commands to do such simple file managment.

How can I do this without logging in as ROOT?

---

### Post by kaamos on 2006-06-08
Own the stuff to you instead of root.

```
sudo chown *your_username*:*your_username* /var/www -R
```

---

### Post by otis_u on 2006-06-08
You're wonderful!

Thank you very much :D

---


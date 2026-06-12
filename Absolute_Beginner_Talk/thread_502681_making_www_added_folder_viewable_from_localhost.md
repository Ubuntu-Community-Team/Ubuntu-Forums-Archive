---
title: "making www added folder viewable from localhost"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-07-16
now i realise that my LAMP won't automatically open index.htm when i browse to a folder

but it does open the index.html automatically tho..

how can i make apache treat .htm similarly?

---

### Post by Al3xK3aton on 2007-07-16
Rename all the HTM to HTML.

---

### Post by jtraub on 2007-07-17
> **manuleka said:**
> how can i make apache treat .htm similarly?

put .htaccess in your www folder that contains
```

DirectoryIndex index.htm

```

---

### Post by Warren Watts on 2007-07-17
Here is a link to the Apache docs for the [DirectoryIndex]("http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex") directive.

Hope this helps!

---


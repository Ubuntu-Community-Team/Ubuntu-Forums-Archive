---
title: "[SOLVED] Help with a script to mass find and replace text files"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-03-18
Hi,

i want to mass edit some html files...

perl -w -i -p -e "s/You are viewing an archived READ ONLY  Forum. For posting please visit our new Forums at <url>www.website.org</url>//g" *.html

sed -i 's/You are viewing an archived READ ONLY Forum. For posting please visit our new Forums at <url>www.website.org</url>//g' /home/firebox/Forum5/HTML/*.html

both get me errors...

I'm trying to delete this line from all files...

You are viewing an archived READ ONLY Forum. For posting please visit our new Forums at <url>www.website.org</url>

thanks !!!!

---

### Post by Cappy on 2008-03-18
```
sed -i 's/You are viewing an archived READ ONLY Forum. For posting please visit our new Forums at <url>www.website.org<\/url>//g' /home/firebox/Forum5/HTML/*.html
```

It has to be <\/url>

---

### Post by PointyWombat on 2008-03-18
You need to escape special characters like / and . with the \ character.

May be easier to just search for a subset of the string and delete it.

such as:
```

sed 's/You are viewing an archived READ ONLY Forum.  For posting//g' file

```

---

### Post by hopelessone on 2008-03-18
what about deleting:

sed -i 's/http://website.org//g' /home/firebox/Forum5/HTML/*.html

how to get around the // part in http://

Thanks for all your help so far BTW

:KS

---

### Post by hopelessone on 2008-03-18
Ahhhh it's not a capital V but \ + / together...

<A HREF="http:\/\/website.org"
<A HREF="../../Ultimate.cgi.html" <<what about the ../../ in here same thing?

---


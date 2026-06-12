---
title: "freemind &amp; text editors fight over filetypes in kde? (mm &amp; txt)"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by jaygo on 2007-10-18
Hi all,
Freemind (a mind-mapping application) has its own filetype :  .mm . After installing this, all .mm files open into Kate (default text editor). When I change .mm to open with Freemind (using right-click > Open With > Freemind > check: remember application association ... ) all .mm files then open in Freemind, **as well as** all txt files. When I change .txt files to open with Kate, all .mm's switch back again.

I read that this is because Linux bases filetype associations on the filetype not on the extension itself. So I checked my /etc/mime.types file and it looks correct as far as I can tell:
```
application/x-freemind				mm
...
text/plain					asc txt text pot
```

Where can I fix this?

---

### Post by jaygo on 2007-10-25
bump.

---

### Post by jaygo on 2007-11-04
Luckily, I finally bumped into the correct place to change it. This is for KDE, which uses Konqueror by default.

[LIST=1]
[*]Open Konqueror
[*]Goto Settings > Configure Konqueror > File Associations
[*]Add the filetype you need (in my case, mindmaps), and assign an application to it.
[*]Remove the extension from any other filetypes where it shouldn't be included.
[*]Hit OK
[/LIST]

---


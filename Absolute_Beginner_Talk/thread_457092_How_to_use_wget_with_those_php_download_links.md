---
title: "How to use wget with those php download links?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-05-28
Hi guys,

I've been using wget for a while now, and absolutely love it. No need for any other download manager. :)

But one thing I need help with though, are those links that are not direct links to the file. For example this link:
[http://www.puppylinux.org/user/downloads.php?cat_id=1&download_id=57](http://www.puppylinux.org/user/downloads.php?cat_id=1&download_id=57)

Normally I'd just type:
```

wget http://www.abc.com/123.avi

```

and download the file, but if I try this way, I'll download the php file instead. Any ideas guys? :)

Cheers,
Kinson

---

### Post by Bachstelze on 2007-05-28
You can't use wget with such links. wget works only if you have the URL of the file.

---


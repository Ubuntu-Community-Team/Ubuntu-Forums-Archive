---
title: "How to delete &quot;-i&quot; file"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by jambalaya on 2008-02-20
Hi.

I created a file that is named -i (for test I wanted to make). Now,when I run rm * in that directory, it bash treats the -i filename as an option (interactive delete) to rm. The question is: how can I delete that file (from bash)? Escaping it doesn't help.

Thanks.

---

### Post by jan quark on 2008-02-20
:confused:

try to rename that file to something more... normal

---

### Post by jken146 on 2008-02-20
Try putting the filename in quotation marks.

---

### Post by amingv on 2008-02-20
Interesting little twitch there, use this:

```
rm ./-i
```

---

### Post by jambalaya on 2008-02-20
Thanks, rm ./-iworks.
I cant rename it since mv also has a -i parameter and is confused by the file.

Cheers.

---

### Post by nick_h on 2008-02-20
You can also use -- to signify the end of an options list.  For example, try:
```
touch -- -i
ls -- -i
rm -- -i
```

---

### Post by jambalaya on 2008-02-21
Wow I haven't heard of that -- thingie. Thanks a lot for that.

---


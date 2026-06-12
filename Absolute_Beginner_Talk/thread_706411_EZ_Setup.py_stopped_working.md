---
title: "EZ_Setup.py stopped working"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by taddy_porter on 2008-02-24
taddy@taddy1:~/download/books$ sudo python ez_setup.py -U hellahella==dev
python: can't open file 'ez_setup.py': [Errno 2] No such file or directory


Above is the error I'm getting when I try to use ez_setup. It used to work, but it no longer does. I'm assuming the file is no longer in my executable path but I don't know how to fix it.

I checked and it is installed still.

---

### Post by rapiscan on 2008-02-24
ez_setup.py installs easy_install,

try typing ```
which easy_install
```

It will tell you where on the path it is (if it exists on the path).  If it's there, you can simply use easy_install instead of python ez_setup.py.

---

### Post by taddy_porter on 2008-02-24
> **rapiscan said:**
> ez_setup.py installs easy_install,

try typing ```
which easy_install
```

It will tell you where on the path it is (if it exists on the path).  If it's there, you can simply use easy_install instead of python ez_setup.py.

That works but I had to call it by the full directory path /usr/bin/easy_install

Shouldn't /usr/bin be in my executable path?

---

### Post by rapiscan on 2008-02-24
Yes, and it is on your PATH if you found it when typing "which easy_install".

I'm not sure why you had to type in the full path, what error do you get when you type it in without the full path?

---

### Post by taddy_porter on 2008-02-24
> **rapiscan said:**
> Yes, and it is on your PATH if you found it when typing "which easy_install".

I'm not sure why you had to type in the full path, what error do you get when you type it in without the full path?

I get the same "can't open file" easy_install message. It did show up in the which search though.

---


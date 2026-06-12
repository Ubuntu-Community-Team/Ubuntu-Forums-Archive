---
title: "What's wrong with this line?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by vuarra on 2007-03-07
This line comes from /etc/apt/sources.list.d/edgy-universe.list, and I had to rem it out in order for any sort of update to happen:
```
#deb http://security.ubuntu.com/ubuntu edgy-security
```

This is line 4, from which I get quite the error message.

Does anyone know why this is a "bad" source?

---

### Post by dwblas on 2007-03-07
I have
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

---

### Post by mand0 on 2007-03-07
It *could* be that the website hosting that is down... So maybe try later or try finding another link to that same package.

::EDIT::

Bah,

I have it as:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe

---

### Post by vuarra on 2007-03-07
@dwblas

thank you very much; that seemed to work.

I can't guarantee that I didn't mess up that file, but I really don't think i did.

---


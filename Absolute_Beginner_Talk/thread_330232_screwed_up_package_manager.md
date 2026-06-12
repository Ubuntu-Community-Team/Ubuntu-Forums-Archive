---
title: "screwed up package manager"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by moosemsan923 on 2007-01-02
i need some help fixing the package manager.

i being a n00b with ubuntu, thought i could just put aurl for a program download in the ACT channel and it would download and install it. i did that and now the package manager will not work to downlaod and install updates, would anyone know how to fix this?

---

### Post by meng on 2007-01-02
(What's the ACT channel? Never heard of it.)
Try posting the output of this command here:
cat /etc/apt/sources.list

---

### Post by taurus on 2007-01-02
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Sef on 2007-01-02
Could you post your sources list?

Open the Terminal (Applications > Accessories > Terminal)

```
gksudo gedit /ect/apt/sources.list
```

---

### Post by moosemsan923 on 2007-01-02
> **meng said:**
> (What's the ACT channel? Never heard of it.)
Try posting the output of this command here:
cat /etc/apt/sources.list

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

[http://download.mozilla.org/?product=firefox-2.0.0.1&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-2.0.0.1&os=linux&lang=en-US)

---

### Post by Sef on 2007-01-02
I see...you need to delete the last line and then your sources list should be ok.

Delete [http://download.mozilla.org/?product...nux&lang=en-US](http://download.mozilla.org/?product...nux&lang=en-US).

That line should not be there.

---

### Post by moosemsan923 on 2007-01-03
how do i delete that line?

---

### Post by MkfIbK7a on 2007-01-03
gksudo gedit /etc/apt/sources.list

---

### Post by moosemsan923 on 2007-01-03
that worked great! thanks for all your help

---


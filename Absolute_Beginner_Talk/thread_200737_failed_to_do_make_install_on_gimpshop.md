---
title: "failed to do make install on gimpshop"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by dronepower on 2006-06-20
I tried to compile [Gimpshop]("http://www.gimpshop.net/"). the ./configure went ok without errors.

The make resulted in the following list : [the make list]("http://squee.nl/make.txt")

When I did make install I only got a bunch of nothing to do, and error 1, and 2's.
The list you can find here: [the make install list]("http://squee.nl/makeinstall.txt")

I use the dutch languaged Ubuntu, so the lists are also in dutch. Sorry bout that.

It would realy give me a good feeling if I succeed in compiling this program :cool: 

What did I do wrong?

---

### Post by taurus on 2006-06-20
Maybe you want to include sudo since you are trying to write to  /usr/local/share/aclocal!!!
```

sudo make install

```

---

### Post by dronepower on 2006-06-20
[QUOTE=taurus]Maybe you want to include sudo since you are trying to write to  /usr/local/share/aclocal!!!
```

sudo make install

```[/QUOTE]


arrghh, stupid me ](*,)   ](*,) 

thanks

---


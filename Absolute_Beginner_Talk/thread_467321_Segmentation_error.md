---
title: "Segmentation error"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by dragunu on 2007-06-07
i am trying to install php4,

however, in the "make" process i am getting the following error:

```

/usr/local/src/php-4.4.7/ext/gd/libgd/gd.c: In function 'gdImageCopyResampled':
/usr/local/src/php-4.4.7/ext/gd/libgd/gd.c:2540: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.

```

thx!!
drag

---

### Post by Cypher on 2007-06-08
Any particular reason you are trying to compile PHP yourself when it's available through APT? Also, any reason you're trying to get 4.4.7 as opposed to PHP5?
```

sudo apt-get install php5

```
on Feisty or
```

sudo apt-get install php4

```
on Edgy, Breezy, Hoary, Dapper seems to b ea easier method..

---


---
title: "internet problems"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by recycledhippy on 2008-02-03
maybe someone can help me out. I just had to do a re-install of Ubuntu 7.10 everything seems to be ok except for the internet. Im using firefox (always have) and everything is slow and choppy. even my typing is lagged, I can type something look up from the keyboard  and watch the words appear after I've typed them. I havent had this problem before and I am using the default version of firefox not the ubutu themed one. thanks for any help this is really bugging me:confused:

---

### Post by pieisgood4589 on 2008-02-03
This is also what happened to me. I just re-installed, and everything was fine. But you could also try to reset xserver and disable compiz...

---

### Post by recycledhippy on 2008-02-03
sorry I am still new here how would I re-set xserver

---

### Post by jan quark on 2008-02-03
do what pieisgood4589 suggested

what are your specs?

have you tried a lighter web browser like kazekahase or epiphany?

do you encounter  any other network problems?

---

### Post by recycledhippy on 2008-02-03
just turned off effects and it's working better which is going to lead me to my next thread. Thanks for the help!

---

### Post by jan quark on 2008-02-03
This code will reconfigure X manually....

```

sudo dpkg-reconfigure xserver-xorg
```

This code will reset X back to default (if the original xorg.conf exists)....

```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---


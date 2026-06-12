---
title: "DSL connection via ubuntu terribly slow"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by MoshNet on 2005-10-18
I have DSL connection. Normally I am running about 512 down and 256 up. However with Ubuntu, it seems my that my MSS and MTU are very low and my recieve windows are very low, I am wondering how I can adjust this. PLease any information would be valuable, I am running slower than dialup nearly with a DSL line.

---

### Post by adwait on 2005-10-18
You can adjust your MTU etc. in /etc/ppp/peers/dsl-connection.

---

### Post by MoshNet on 2005-10-19
I do not have that file...

I have

```

provider
wvdial
wvdial-pipe

```

I mean I am dragging along here, ridiculous. It's so slow I feel like ditching ubuntu...

---


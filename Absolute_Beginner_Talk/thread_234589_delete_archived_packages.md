---
title: "delete archived packages?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-08-11
when u install updates the downloaded stuff becomes archived



how do you delete them cause i wanna save up some space

---

### Post by ovimunt on 2006-08-11
Type:

```

sudo aptitude clean

``` Anyway, all the packages get downloaded in:
```

/var/cache/apt/archives

``` You can get in there and manually delete those you don't need or backup those that you want to keep for later so you won't have to download them again if you ever need them once more.

---

### Post by bhoughton on 2006-08-11
Provided that you create a backup CD of those archive files, how do you go about reinstalling them?

---


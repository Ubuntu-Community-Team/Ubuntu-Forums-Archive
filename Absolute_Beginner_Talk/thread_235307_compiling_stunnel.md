---
title: "compiling stunnel"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by Espion on 2006-08-12
I downloaded the stunnel source and tried to compile it. I used this command line in the terminal:
```
./configure --with-ssl=/usr/lib/ && make && sudo make install
```

And it gets so far then gives me this error:
```
checking for SSL directory... Not found

Couldn't find your SSL library installation dir
Use --with-ssl option to fix this problem
```

I tried using --with-ssl and pointing it to various directories but it was no use.

I just installed ubuntu a few hours ago so I know pretty much nothing about it or linux. Any help would be appreciated.

---

### Post by Perfect Storm on 2006-08-13
Make sure you have libssl-dev installed.

```
sudo apt-get install libssl-dev
```

---

### Post by Espion on 2006-08-13
Thanks, I try this again as soon as I get a chance :)

---


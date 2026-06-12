---
title: "compiling programs"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by xGutsAndGloryx on 2007-10-21
i am having a tough time compiling programs.. they always have dependencies... i try find them but some won't install. is there any easier way to do this?

---

### Post by FuturePilot on 2007-10-21
Not really. What are you trying to compile? Have you looked in the repos to see if it's there? If you're not following any guides for what you're trying to compile, you pretty much have to go by the errors from ./configure

---

### Post by nchase on 2007-10-21
```
sudo apt-get build-dep programname
```

the above command can be very helpful if you're trying to compile a newer/different version of a program that is in the repositories.

---


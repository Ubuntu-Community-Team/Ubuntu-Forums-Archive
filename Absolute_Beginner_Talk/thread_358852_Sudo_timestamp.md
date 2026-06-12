---
title: "Sudo timestamp?"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-02-11
When I try to update (sudo apt-get update), this is the response I get:

```
sudo: timestamp too far in the future: Feb 12 14:44:46 2007
```

I'm getting really frustrated, 'cause Windows erased my entire HD (w/o my consent! ha).

Please help :)

---

### Post by taurus on 2007-02-11
Try to reboot and run that command again.

```
sudo apt-get update
```

---

### Post by kbsuperstar on 2007-02-11
Didn't work. Same result.

Any other ideas?

---

### Post by aysiu on 2007-02-11
Reboot.

---

### Post by wildkarde on 2007-02-11
Uh, i may be way off, but just for kicks, type this on the console.

```
date
```

---

### Post by ticklecricket on 2007-02-11
ooh, I had this happen to me once, and I half forgot how I fixed it. If I remember correctly, first you should check what time your computer thinks it is with

```
 date
```

if that's wrong you need to reset it to the correct time. Then clear sudo's cache with

```
sudo -K
```

then try it again. I hope that works, if it doesn't do some more searching on the forums, I bet there's some more on the topic.

---


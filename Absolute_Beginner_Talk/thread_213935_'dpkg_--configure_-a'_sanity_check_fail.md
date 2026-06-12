---
title: "'dpkg --configure -a' sanity check fail"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by anubis2814 on 2006-07-12
I am having problems, using ubuntu 6.06 for AMD64(I know I was naive when buying the thing) it's been freezing up alot and now I can't install anything.  it tells me this
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
When I type that into the terminal it tells me only a superuser can do that.
Please help.

---

### Post by K.Mandla on 2006-07-12
Try it with 'sudo' in front. In other words. ...

```
sudo dpkg --configure -a
```
It will ask for your password. 

That should do the trick. If you run into any more problems, just ask. :)

---


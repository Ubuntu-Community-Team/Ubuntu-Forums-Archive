---
title: "Running Heron in Virtualbox"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by bitterbug on 2008-02-07
I figured I'd take a look at hardy in virtualbox, but I can't get past the login screen.
My guess is that compiz is trying to start, and since the VM doesn't have acceleration it's choking.

How would I disable compiz from the console login?

---

### Post by talsemgeest on 2008-02-07
```
touch $HOME/.config/compiz/disable-compiz
```

---


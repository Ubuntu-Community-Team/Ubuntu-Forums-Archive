---
title: "[SOLVED] Envy"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Emmazing on 2008-03-12
After a recent reformat, I have just reinstalled Ubuntu Feisty and I need to use Envy to get my video card working right. I've used this program before and it worked great. When I go to the website and download it, I have trouble running it. It says the following...
Error: the dependency is not satisfiable: build-essential
I have universe and multiverse on as well so it's not that.
I'm completely lost as to what's going wrong. This didn't happen last time I used it.
Thanks for any help you can offer

---

### Post by rune0077 on 2008-03-12
You just need to install the package called build essential. Search for it in Synaptic and then install it and that should do the trick.

---

### Post by taurus on 2008-03-12
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by hhhhhx on 2008-03-12
sudo apt-get install build-essential

EDIT: too late o___0

---

### Post by Emmazing on 2008-03-12
Thanks that's what I needed. strange that I did have to do that before.

---

### Post by rune0077 on 2008-03-12
> **Emmazing said:**
> Thanks that's what I needed. strange that I did have to do that before.

You need build-essential for lots of packages, so chances are you just installed it with something else before installing Envy the last time.

---


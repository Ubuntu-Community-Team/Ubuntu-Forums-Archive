---
title: "Failure to add software/Reinstall Feisty"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by BaronSantiago on 2007-08-12
Having worked through various problems with Feisty (network, undetected monitor etc) I tried to load various new software.

After a few packages installed successfully, I tried to install K3b. I tried Add/Remove, Synaptic and the terminal. It said it installed but it didn't.

I immediately uninstalled what was said to be there.

Now Add/Remove freezes and synaptic works only intermittently.

I guess I may have to re-install Feisty. What is the best way to do this without starting from the very beginning?

---

### Post by Bofur on 2007-08-12
Have you tried uninstalling the software with terminal using:
```
sudo apt-get autoremove k3b
```
Then reinstalling?

---

### Post by BaronSantiago on 2007-08-12
Thanks.

Just tried that, but it says cannot find K3b, so I guess it is uninstalled. Problems still remain.

---

### Post by 1/0 on 2007-08-12
Are you using Compiz Fusion? In that case try: 

```
sudo metacity --replace
```

---


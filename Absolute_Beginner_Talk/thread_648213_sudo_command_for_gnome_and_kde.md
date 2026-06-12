---
title: "sudo command for gnome and kde?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-12-23
i just want to get this clarified.


to install wine in ubuntu i will type the command

> sudo aptitude install-wine


and to do the same in kde i will have to write

> kdesu aptitude install-wine


have i got this right??

---

### Post by LaRoza on 2007-12-23
> **faraz_k86 said:**
> 
have i got this right??

No. Use sudo in both. Only use different commands for a graphical app.

---

### Post by faraz_k86 on 2007-12-23
can u please provide an example?

---

### Post by LaRoza on 2007-12-23
> **faraz_k86 said:**
> can u please provide an example?

Since aptitude doesn't have a GUI, you use sudo (in all *buntu's)

```

sudo aptitude install build-essential

```

In GNOME, for GUI apps, you use:

```

gksudo synaptic

```

In KDE:
```

kdesu synaptic

```

Run the last two commands, and you will see what they do. (They will only open Synaptic Package Manager)

---

### Post by kzutter on 2007-12-23
Additional note:
the original poster's commands will fail for another reason:
install-wine is neither a command nor is it a package.

This is correct syntax for aptitude from a terminal session:
```
sudo aptitude install  wine

```

---

### Post by jonward690 on 2007-12-23
Ok but remember on kubuntu if you are wanting to run a program over a gui you have to use kdesudo I no wierd but on gnome it is gksu.

---


---
title: "installed synaptic , but i can't run it"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-14
it appears i have it installed in the "Add/remove.." tool, but i can't find it in applications. :( 
where is it?

---

### Post by shareMenaPeace on 2007-02-14
Hmm i think synaptic is installed per default.

You normaly can access synaptic by typing synaptic into the termrinal or use

System -> Administration -> Synaptic Package Manager

---

### Post by DerHesse on 2007-02-14
in text box use:

```
$ **sudo** synaptic
```

---

### Post by DerHesse on 2007-02-15
or is it that you are looking for?

/usr/bin/gnome-app-install

---

### Post by Tomosaur on 2007-02-15
> **DerHesse said:**
> in text box use:

```
$ **sudo** synaptic
```

You should use **gksudo** for graphical apps:
```

gksudo synaptic

```

---

### Post by DerHesse on 2007-02-16
> **Tomosaur said:**
> You should use **gksudo** for graphical apps:
```

gksudo synaptic

```
Interesting. Do you know the reason for that?

---


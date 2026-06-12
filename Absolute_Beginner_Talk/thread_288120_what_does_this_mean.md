---
title: "what does this mean?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-10-29
with edgy, i'm finally able to use scratchpad (text editor). i can right-click on a text file and open it in scratchpad, no problem. when i try to open it via the terminal, with 'sudo', i get this error - *Segmentation fault (core dumped)*. what's up with that?

---

### Post by taurus on 2006-10-29
How did you install it?  Did you install it from repos, from source, or a binary from somebody?  What does these two commands report about your scratchpad?

```
file /usr/bin/scratchpad
ldd /usr/bin/scratchpad
```

---

### Post by fuscia on 2006-10-29
> **taurus said:**
> How did you install it?  Did you install it from repos, from source, or a binary from somebody?  What does these two commands report about your scratchpad?

i installed it from source.

```
file /usr/bin/scratchpad
```

gets - */usr/bin/scratchpad: ERROR: cannot open `/usr/bin/scratchpad' (No such file or directory)*

```
ldd /usr/bin/scratchpad
```

gets - [i]
ldd: /usr/bin/scratchpad: No such file or directory[/i]

thanks for the response.

---

### Post by picpak on 2006-10-29
Try running

```
whereis scratchpad
```

so we know where it is.

---

### Post by fuscia on 2006-10-29
> **picpak said:**
> Try running

```
whereis scratchpad
```

so we know where it is.

e voila - */usr/local/bin/scratchpad*

---

### Post by picpak on 2006-10-29
Cool. Now, it could be as simple a matter as having to use gksudo instead of sudo. Try running

```
gksudo scratchpad
```.

---

### Post by fuscia on 2006-10-29
> **picpak said:**
> Cool. Now, it could be as simple a matter as having to use gksudo instead of sudo. Try running

```
gksudo scratchpad
```.

there was a flash, and then, nothing happened. this might be a sign to return to my beloved and faithful nano.

---


---
title: "silly question about deleting protected shortcuts [Resolved]"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by TriNitro on 2007-04-03
Ok, so Edgy came with this cool shortcut on the home directory of examples.  Kinda interesting, kinda helpful, but not after more than 5 minutes of having it installed.  Because I love things being clean, I wanted to remove the shortcut for these examples, and nothing.  I drag-dropped into trash, hit the delete button and right click delete, but nothing.  I'm guessing it's because of that huge lock icon in the corner that I somehow missed before, but I don't have permission to change it. What can I do to remove a stinking shortcut?

SHORT VERSION
How do I delete the protected "Examples" shortcut on the Home directory?

---

### Post by dbbolton on 2007-04-03
try this ```
sudo rm ~/Examples
```

---

### Post by aysiu on 2007-04-03
I've always been able to delete the Examples folder. That's odd.

I guess you can try one of these methods and delete it as root:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by aysiu on 2007-04-03
> **dbbolton said:**
> try this ```
sudo rm ~/Examples
```
While technically correct, I would be **very** wary of *ever* typing or pasting these two commands into the terminal right next to each other: ```
sudo rm
``` Accidental bad things could happen depending on what you type or press after those two commands.

---

### Post by TriNitro on 2007-04-03
thanks, I remembered how to remove something with the sudo rm command before I checked back. It did the trick. thanks all

---

### Post by TriNitro on 2007-04-03
yeah, I geuss that could easily get someone into trouble

---


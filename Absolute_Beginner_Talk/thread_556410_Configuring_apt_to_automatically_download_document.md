---
title: "Configuring apt to automatically download documentation packages"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Marcipicus on 2007-09-21
Hi I want to configure apt-get to automatically download the info pages for the programs that i download. I manually downloaded the apt-doc package but it isn't coming up when I type info apt (apt-get, etc).

So I was hoping to find out what exactly I would have to do to automatically download the documentation if it's possible. I would prefer to change configuration files if there's an option or variable in there (as opposed to adding a command option) but if I can set it up to automatically download all suggested packages that would work as well.

Thank you to anyone one who can get me on the right track here

---

### Post by ijason on 2007-09-21
hey

i'm new at this, but i'm pretty certain that the apt-get command is strictly command driven. i don't think it's intended or designed to automatically get dependent packages. 

synaptic package manager on the other hand, will make it easy enough to get documentation or dev packages. **system>admin>synaptic package manager**

---

### Post by mysticmatrix on 2007-09-21
> **Marcipicus said:**
> Hi I want to configure apt-get to automatically download the info pages for the programs that i download. I manually downloaded the apt-doc package but it isn't coming up when I type info apt (apt-get, etc).

So I was hoping to find out what exactly I would have to do to automatically download the documentation if it's possible. I would prefer to change configuration files if there's an option or variable in there (as opposed to adding a command option) but if I can set it up to automatically download all suggested packages that would work as well.

Thank you to anyone one who can get me on the right track here

For any program you download, documentation is usually in /usr/doc

For any command

```
man <commandname>
```

provides best info.

---


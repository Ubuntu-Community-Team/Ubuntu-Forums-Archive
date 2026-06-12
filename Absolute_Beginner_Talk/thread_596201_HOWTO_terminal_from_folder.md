---
title: "HOWTO: terminal from folder"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by sitka on 2007-10-29
how can you right click on a folder let's say from your desktop --> open with terminal?

saw that other post regarding the nautilus terminal that doesn't seem to do the trick

---

### Post by rax_m on 2007-10-29
Hi
You can install the "nautlius-actions" package from the synaptic package manager. 
You might have to do some configuring to add an action that says "open terminal at this directory". Sorry I can't help you with the config, but I know the tool can do it.

Here's a link to the features:
[http://www.grumz.net/?q=taxonomy/term/2/9](http://www.grumz.net/?q=taxonomy/term/2/9)

good luck 
Rax

---

### Post by oldos2er on 2007-10-29
You need to restart X.

---

### Post by steve.horsley on 2007-10-29
I enabled that trick by installing package nautilus-open-terminal.

---

### Post by stchman on 2007-10-29
> **sitka said:**
> how can you right click on a folder let's say from your desktop --> open with terminal?

saw that other post regarding the nautilus terminal that doesn't seem to do the trick

You need to install a package called nautilus-open-terminal.

```
sudo apt-get -y install nautilus-open-terminal
```

It is one of those things that need to be installed.  Once installed you will be able to right mouse click in Nautilus and open a terminal in that folder.

---

### Post by Vadi on 2007-10-29
Here's a link to a bunch of very useful nautilus scripts, including an "open terminal here" and 'edit file with root privs" ([click]("https://help.ubuntu.com/community/NautilusScriptsHowto?highlight=%28nautilus%29#head-92d3e7b154d21f493b56814da43900444dad4430")).

---


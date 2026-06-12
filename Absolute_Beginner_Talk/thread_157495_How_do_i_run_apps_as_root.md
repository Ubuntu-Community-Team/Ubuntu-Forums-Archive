---
title: "How do i run apps as root?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Ob1 on 2006-04-09
I recived this message with one of my applications

```
You are NOT root- some options are not available
```

---

### Post by JAwuku on 2006-04-09
To run a command as root, you simply at **sudo** as a prefix.

So, for example to edit your repositories file, you would type:
```
**sudo** gedit /etc/apt/sources.list
```

For a GUI application, you would use **gksu** instead.

For example, to access synaptic, you type:
```
**gksu** synaptic
```

and then type in your password.

Note, in Ubuntu/Kubuntu, there is no separate root password, just type in your own user password.

---

### Post by aysiu on 2006-04-09
[QUOTE=JAwuku]
For a GUI application, you would use **gksu** instead.

For example, to access synaptic, you type:
```
**gksu** synaptic
```

and then type in your password.[/QUOTE] Isn't it ```
gksudo synaptic
```?

---


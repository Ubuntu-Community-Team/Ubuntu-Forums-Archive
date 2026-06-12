---
title: "Virt-manager opens then closes"
date: 2023-10-21
forum: Arch and derivatives
---

### Post by boyobiscuits on 2023-10-21
when i open virt-manager on artix linux it opens then closes

---

### Post by The Cog on 2023-10-21
Try launching it from the terminal and see if it prints any error messages. The command is **virt-manager**.

---

### Post by coffeecat on 2023-10-21
Not Ubuntu. Moved to *Arch & Derivatives*.

---

### Post by boyobiscuits on 2023-10-21
i get this:
```
Traceback (most recent call last): 
  File "/usr/bin/virt-manager", line 6, in <module> 
    from virtManager import virtmanager 
  File "/usr/share/virt-manager/virtManager/virtmanager.py", line 13, in <module> 
    import gi 
  File "/usr/lib/python3.11/site-packages/gi/__init__.py", line 40, in <module> 
    from . import _gi 
ImportError: /usr/lib/python3.11/site-packages/gi/_gi.cpython-311-x86_64-linux-gnu.so: undefined symbol: g_asse
rtion_message_cmpint

```

---

### Post by MAFoElffen on 2023-10-21
One thing that I would check first, Virtual mager depends on the libvirtd daemon to be running before it can start.

Please... If you are posting commands or raw output, post them within CODE Tags. If you do to how to do that... From EDit or the New Post editor, select "Go Advanced" to open the Advanced Editor with the extended tool bar... If you have raw out posted like your last post, select the raw output with your mouse > Select the "#" Icon to wrap that selected text with CODE Tags. To post new with same, select the "#" icon to insert the tags and paste your commands and/or raw output within the tags...

Pleas post the reuslt of this within CODE Tags:
```

sudo systemctl status libvirtd --no-pager

```

---

### Post by boyobiscuits on 2023-10-21
i got this 
```
 [FONT=monospace][COLOR=#000000]sudo: systemctl: command not found[/COLOR][/FONT] 
```

---


---
title: "gdesklet error.... Why Alway me"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by jinxs1591 on 2007-07-30
please help 



  === Unhandled error! Something bad and unexpected happened. ===

[EXC]list index out of range
in /usr/lib/gdesklets/gdesklets-shell: line 9 ?
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 52 get_plugin
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 40 get_plugins_by_pattern
in ./Shell/__init__.py: line 70 init
in /usr/lib/gdesklets/shell/Plugin.py: line 18 _get_plugins_by_pattern
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 40 get_plugins_by_pattern
in ./Profiles/__init__.py: line 24 init
in ./Profiles/__init__.py: line 39 __build_menu
in ./Menu/__init__.py: line 169 set_check_item
in ./Menu/__init__.py: line 79 __set_node
[EXC]/usr/lib/gdesklets/shell/plugins/Menu/__init__.py

[---]   74             if (not submenu):
[---]   75                 submenu = gtk.Menu()
[---]   76                 pitem.set_submenu(submenu)
[---]   77
[---]   78         parent, index = self.__get_node(path)
[ERR]>  79         name, nil, children = parent[index]
[---]   80         parent[index] = (name, item, children)
[---]   81         submenu.insert(item, index)
[---]   82
[---]   83
[---]   84
[---]   85     #

---

### Post by Pragmatist on 2007-07-31
When and where do you get this message?

---

### Post by sailor2001 on 2007-07-31
I think you should change your name

---

### Post by Pragmatist on 2007-07-31
> **sailor2001 said:**
> I think you should change your name

What is your advice?

---

### Post by jinxs1591 on 2007-08-01
It happen everytime I try to start gdesklet

---

### Post by Pragmatist on 2007-08-02
> **jinxs1591 said:**
> It happen everytime I try to start gdesklet

Have you tried completely uninstalling and then reinstalling gdesklets?  

Which desklets are you running?

---

### Post by jinxs1591 on 2007-08-04
> **Pragmatist said:**
> Have you tried completely uninstalling and then reinstalling gdesklets?  

Which desklets are you running?

I have uninstalled and reinstalled And still all it does is start up hang on screen and crash. Really I havent been able to run any desklets since the program wont start

---

### Post by Pragmatist on 2007-08-05
How about a system update?

Here is one way to do it:

```
sudo apt-get update
```

and then,

```
sudo apt-get upgrade
```

---

### Post by nitro_n2o on 2007-08-05
what is your python version?

---

### Post by esc1 on 2007-08-05
Try Screenlets.  I think its better IMO.

---


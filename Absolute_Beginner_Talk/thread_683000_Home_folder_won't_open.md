---
title: "Home folder won't open"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-01-30
I don't know how or why this happened, but at the moment whenever I open my home folder, the window just freezes up. I checked system monitor and nautilus was taking 49-50% of my cpu. Moreover, if i close it by force quitting it, another home folder just opens up and freezes again. My only option is to kill nautilus. I tried rebooting but the results were the same. I am running feisty FYI.

---

### Post by Masterj15 on 2008-01-30
give your specs. For right now search through the terminal. If its a graphical error then the terminal will get what you need.

---

### Post by philinux on 2008-01-30
I'd try deleting the /home/user/.nautilus folder.

You'll have to use rm or use konqueror.

---

### Post by intense.ego on 2008-01-30
> **Masterj15 said:**
> give your specs. For right now search through the terminal. If its a graphical error then the terminal will get what you need.

Specs - Lenovo thinkpad t60
1.83 ghz intel core duo
512 mb ram
is there anything else you need to know?

What would happen if i deleted nautilus?

---

### Post by philinux on 2008-01-30
/home/user/.nautilus is only the config file folder. It will get re-generated next time you run nautilus.

Worth a shot.

---

### Post by xc3RnbFO8P on 2008-01-30
Reinstall nautilus

---

### Post by corevette on 2008-01-30
run 
```
nautilus
```
in the terminal and direct to your home directory
do any unusual outputs appear?

---

### Post by Charcoal1981 on 2008-01-30
You could also try:
```
nautilus -c
```
and see what outputs it gives if any

Also, does this happen only for your home folder or any folder opened in nautilus

---

### Post by intense.ego on 2008-01-31
I got this for nautilus -c

```
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory

```

---


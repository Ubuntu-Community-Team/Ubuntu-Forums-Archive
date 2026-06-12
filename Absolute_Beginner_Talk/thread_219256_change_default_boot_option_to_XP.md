---
title: "change default boot option to XP"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by cgc1400 on 2006-07-19
Hello fans,

To save someone some time, here is how to change the default boot option to XP.
1. open a terminal in Ubuntu
enter this:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst


2.  * Find this line 

...
default     0
...

3.   * Replace with the following line 

default     6 

(6 in my case, refers to the order that XP is located in my boot list. Ex: XP is number **[COLOR="Red"]6[/COLOR]** in the list or it could be number 2 in your list)

    * Save the edited file 8) 

I hope this helps.

source: [http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu](http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu)


seen:cool:

---

### Post by jpmorelli on 2006-07-19
Who wants the default option set in Win XP !? ....:confused: 

just a joke ! too many people is just starting and this really helps them. ( like me )

---

### Post by taurus on 2006-07-19
Actually, if XP is the 6th entry, then it should have been

```

default 5

```
Since Linux (or Unix) counts from 0, not 1 (like that crappy Windows thing)!!!  ;)

---

### Post by kinematic on 2006-07-19
lilo actually counts from one ;)

---


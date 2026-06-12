---
title: "can't rename applications :'("
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by xkendrax on 2007-07-31
I have this problem, i do what its supposed to (right click on applications menu, properties, select application, properties, change name) but the application stays the same,what can i do?

---

### Post by silent1643 on 2007-07-31
hmm sounds like your using Nautilus
try [this]("http://www.littleubuntu.com/v2/search.php?search=sudo")

or  if you are trying to change the name of the shortcut in your menu goto -system->preferences->main menu
then select the program you want to rename and click properties

---

### Post by bodhi.zazen on 2007-07-31
I do not know what you are trying to do exactly ...

You can make a link 

```
sudo ln -s /app/to/link /usr/bin/new_cool_name
```

Or set an alias in ~/.bashrc

```
alias Cool_new_name='/path/to/old/name'
```

---

### Post by xkendrax on 2007-07-31
Thank you, how do i run nautilus with admin privileges or admin mode?

---

### Post by ugm6hr on 2007-07-31
> **xkendrax said:**
> Thank you, how do i run nautilus with admin privileges or admin mode?

```
gksudo nautilus
```

---

### Post by xkendrax on 2007-08-01
:( I still cant, i did system->preferences->main menu, selected the application properties, changed the name but the name reverts to the original, im so frustrated i think im gonna cry.

---


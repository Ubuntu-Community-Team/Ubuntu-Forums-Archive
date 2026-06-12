---
title: "Mysql where?"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by jjtoymachine on 2007-02-19
Where are the MySQL databases stored in Ubuntu? 

:KS :KS

---

### Post by nereid on 2007-02-19
I would think in /usr/share/mysql but I could be wrong.

---

### Post by jjtoymachine on 2007-02-19
doesnt seem to be there 

:(

---

### Post by twowheeler on 2007-02-19
Try /var/lib/mysql, that's where they are on my machine.

In general when you want to find something, try entering 'locate filename' in a terminal.

---

### Post by jjtoymachine on 2007-02-19
> **twowheeler said:**
> Try /var/lib/mysql, that's where they are on my machine.

In general when you want to find something, try entering 'locate filename' in a terminal.

Thanks mate! thats where they are.

:KS :KS

---

### Post by hyper_ch on 2007-02-19
> **twowheeler said:**
> Try /var/lib/mysql, that's where they are on my machine.

In general when you want to find something, try entering 'locate filename' in a terminal.


first you have to build the slocate database:

```

sudo updatedb

```

---


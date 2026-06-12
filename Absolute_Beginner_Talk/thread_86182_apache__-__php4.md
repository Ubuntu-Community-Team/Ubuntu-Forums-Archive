---
title: "apache  -  php4"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by sunrex on 2005-11-04
i looked it up but didint find what i was looking for

testphp thing worked...but if i  try e107
> 
Warning: Unknown(/var/www/index.php): failed to open stream: Permission denied in Unknown on line 0

Warning: (null)(): Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

im guessing i need to add index.php to the index files...my question is HOW and WERE

thanks in advanced.

sunrex

---

### Post by John.Michael.Kane on 2005-11-04
You may want to see what is in there. mind you this is a shot in the dark. however worth a try. 

```
sudo gedit /var/www/index.php
sudo gedit /usr/share/php:/usr/share/pear
```

---

### Post by sunrex on 2005-11-04
theres nothing in sudo gedit /usr/share/php:/usr/share/pear

and it appears even if i add a folder, when i try to go there. it says i dont have premission...so what do i need to do to get...ya know what somone just give me there apache2 config plz

---


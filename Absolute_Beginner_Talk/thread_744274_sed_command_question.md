---
title: "sed command question"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by opscure on 2008-04-03
Here's a quick tutorial link on finding and replacing. 

[http://www.brunolinux.com/02-The_Terminal/Find_and%20Replace_with_Sed.html](http://www.brunolinux.com/02-The_Terminal/Find_and%20Replace_with_Sed.html)

Remember you can always use:

```
man sed 
```

to view the sed manual page.

---

### Post by Windy_Red_Sea on 2008-04-03
try this:

sed -i 's/\s\+//g' fileName

explanation:
-i --> edit file in place

's/\s\+//g' -->   s = substitute
                       \s = white space
                       \+ = one or more
                       //  = replace with nothing
                       /g = globally 

fileName --> name of the file you want to modify

Regards,
Frank

---


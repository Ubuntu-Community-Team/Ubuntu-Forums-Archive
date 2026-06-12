---
title: "GDM trouble after ram upgrade."
date: 2007-10-26
forum: Apple Intel Users
---

### Post by excrabot on 2007-10-26
Hey there,

after i upgraded the ram in my macbook C2D  from 1G to 1.5G yesterday i get this error message at login..

'GDM could not write to your autorisation file'

to complicate the problem i cant acces the terminal using 'control+alt+F1' , there's no response when i try that combo or 'alt+F1' either. I haven't added any new files or altered any programs, just the ram. OSX still works fine.

any ideas..

---

### Post by alephsmith on 2007-10-26
Remember that on macs the function keys act as hardware controls, so to  activate function keys for software controls you need to use the fn modifier.

Try fn+control+alt+F1

---

### Post by kast on 2007-10-26
Can you boot Ubuntu to the safe mode kernel? Just to get to the Root Prompt

---

### Post by excrabot on 2007-10-26
Thanks guys, adding Fn to the combo works fine, now i can start to fiddle some more.

---

### Post by kast on 2007-10-26
do a **df** make sure you have enough disk space

---

### Post by excrabot on 2007-10-26
Yes, i just did and was surprised to see that i have indeed maxed out at 115G. i've never found a hard drive i couldn't fill. 

thanks again.

---


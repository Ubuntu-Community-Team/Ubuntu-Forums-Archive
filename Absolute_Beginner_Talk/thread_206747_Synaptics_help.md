---
title: "Synaptics help"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by RajivNair on 2006-06-30
whenever i start synaptics i get the following error and the package list shows empty and i have to reload all the time 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

Can anyone tell me what the problem might be.


Thanks in advance.

---

### Post by invalid on 2006-06-30
[QUOTE=RajivNair]whenever i start synaptics i get the following error and the package list shows empty and i have to reload all the time 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

Can anyone tell me what the problem might be.


Thanks in advance.[/QUOTE]
It sounds like it may have been exited during an install process. It happens on occasion.

Have you tried the suggestion? Open a terminal and type:
```
sudo dpkg --configure -a
```
That should fix it right up.

---

### Post by atoponce on 2006-06-30
[quote=RajivNair]whenever i start synaptics i get the following error and the package list shows empty and i have to reload all the time 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

Can anyone tell me what the problem might be.


Thanks in advance.[/quote] 
Pull up your terminal and run

```
dpkg --configure -a
```

---


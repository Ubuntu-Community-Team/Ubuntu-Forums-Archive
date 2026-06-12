---
title: "how do i uninstall wine in xubuntu 7.10?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by nexttry on 2008-02-23
i just want to remvoe wine and nothing else. i tried once but the computer froze and cant uninstall so i think i got some what half a program.

thanks

---

### Post by PmDematagoda on 2008-02-23
Try removing Wine using the terminal by executing:-
```
sudo apt-get purge wine
```

---

### Post by nexttry on 2008-02-23
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

my late answer is cause of the freezing os.

it also says kernel panic when i try to start sometimes
why is that?
had to write quick thus in this window

---

### Post by PmDematagoda on 2008-02-23
Execute:-
```
sudo dpkg --configure -a
```
and
```
sudo apt-get install -f
```
Post any and all error messages that you receive.

---

### Post by JoshuaRL on 2008-02-23
You can also try going into System->Administration->Synaptic Package Mangager.  Then go to the filters, open the "Broken" filter and select all there for reinstallation.

You can try that if the suggestions from PmDematagoda don't work.

---


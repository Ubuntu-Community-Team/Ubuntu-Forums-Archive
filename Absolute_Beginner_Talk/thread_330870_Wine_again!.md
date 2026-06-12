---
title: "Wine again!"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-01-03
why does programs can't be uninstalled from wine? even if I try with ```
sudo wine uninstaller
``` they are still there, even if I remove, or complete remove wine from the synaptic they are still there!
And that leaded  me to see that even if I gave complete removal on synaptic, wine still has t he same configuration and programs, how do I control the COMPLETE removal of programs as wine?

---

### Post by 23meg on 2007-01-03
Installed apps and configuration files are in your ~/.wine directory. You can delete them.

---

### Post by Jorge32 on 2007-01-03
> **23meg said:**
> Installed apps and configuration files are in your ~/.wine directory. You can delete them.

and where is the  ~/.wine directory located usually?

---

### Post by Jeremy Jackins on 2007-01-03
~ is the same as your home directory. /home/(username)/.wine would be another way of putting it.

---

### Post by Jorge32 on 2007-01-03
ok ok, I've tried to erase any trace of the programs, I even erased evyrhint that had to be with them on the regedit, but they are still appearing at the applications menu, on others, and they still appear on ```
wine uninstaller
```
what's the problem here!?

---

### Post by Jorge32 on 2007-01-03
> **23meg said:**
> Installed apps and configuration files are in your ~/.wine directory. You can delete them.

by deleting the complete folder eveyrhing relationed to wine will be erased?

---

### Post by Jorge32 on 2007-01-03
I've already deleted every folder in my user, uninstalled it fromsynaptic and it stills get the same way when I re-install it? can anyone tell me the way of completely removing wine please?




Forget about it, it seems it worked for me the

 sudo aptitude remove wine



**uuuhm again I installed it and it was the same! Again apps at the applications menu, again everything , why is it happening? why?**

---


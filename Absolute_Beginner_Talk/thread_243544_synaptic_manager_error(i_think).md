---
title: "synaptic manager error(i think)"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by mykalreborn on 2006-08-25
i've just installed ubuntu for less than a day now, so i really don't understand much of what's going on here.
i restarted the system and when it turned on again i got an error:"please run package manager[...]or apt-get on a terminal[...]the error message was:'error:opening the cache(E:type'sudo'is not known on line 35 in source list/etc/apt/sources.list,E:the list of sources could not be read.)'"
i opened the package manager, but it still had the same error.

---

### Post by TFX360 on 2006-08-25
There is most probably an error in your sources.list

Show us the insides of your apt sources.list


Open a terminal and type:
```
gksu gedit /etc/apt/sources.list
```

and paste the contents here.


Kind regards,


TFX

---


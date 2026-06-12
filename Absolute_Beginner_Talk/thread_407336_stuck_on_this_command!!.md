---
title: "stuck on this command!!"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by painsponge on 2007-04-12
hey everyone,

I was following the Binary Drive How to for ATI graphic card installation, i did everything till this line, 

 bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy

I replaced <version> with 8.35.5-x86.x86_64,  the full file name is ati-driver-installer-8.35.5-x86.x86_64.run.

but all i get is the file, directory doesn't exist.  i tried moving the file to a new folder, and changing the name, but it simply refuse to work.  its driving me nuts!!

please shed some light in this newb's frustrated situation... 

thanks

---

### Post by Bachstelze on 2007-04-12
Tab might help you to get the file name written correctly :)

---

### Post by justleen on 2007-04-12
> **HymnToLife said:**
> Tab might help you to get the file name written correctly :)

Tab is your friend.. just type the first few letters, hit tab, and it wil auto complete (or give you as list if more then  one file matches.. )

---

### Post by painsponge on 2007-04-12
thanks for the replies, 
i tried tab, still no luck. i can see the file on the desktop, but the damn command can't find it :confused: . 


argg :(

---

### Post by Famicommie on 2007-04-12
Are you including the phrase "bash"? It should simply be
./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy

---

### Post by dreadlord_chris on 2007-04-12
> **painsponge said:**
> thanks for the replies, 
i tried tab, still no luck. i can see the file on the desktop, but the damn command can't find it :confused: . 


argg :(

bet you're not in your Desktop folder when you're trying to run that file...

open a terminal:
```

cd Desktop
bash ./ati-driver-installer-8.35.5-x86.x86_64.run  --buildpkg Ubuntu/edgy

```

and, uh, not sure, but you might need to *sudo bash ./ati.....*

---


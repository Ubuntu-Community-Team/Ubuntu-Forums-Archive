---
title: "more problems with gcc and compiling"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by proventech on 2006-01-06
ok, i just installed ubuntu on my P4 and it is working good, but i again have problems installing ksmoothdock.
I installed apt-get gcc, build-essentials, xlibs-dev, and qt3-apps-dev.
I ran ./configure and it passed just fine.  when i ran make, it came back with 
collect2:  ld returned 1 exit status
make [2]: *** [ksmoothdock] Error 1
make [2]: Leaving directory '/home/proventech/ksmoothdock/scr'
make [1]: *** [all-recursive] Error 1
make [1]: Leaving directory '/home/proventech/ksmoothdock'
make: *** [all] Error 2

Anyone have any ideas?

Thanks in advance

---

### Post by proventech on 2006-01-07
no one have any ideas?

---

### Post by nalmeth on 2006-01-07
[http://www.ubuntuforums.org/showthread.php?t=45408](http://www.ubuntuforums.org/showthread.php?t=45408) 
tried this yet? A .deb is referred to in the first reply. know how to install .deb s? I'm sorry if this is a insulting/redundant question, because compiling is a lot harder than installing debs, but it is absolute beginner talk.  I think I may try this when I get back to my computer. I am always looking for more eye candy :D

EDIT:
If you really would like to compile, aparently you will need this other tools for this particular app aswell:
> sudo apt-get install libqt3-mt-dev libqt3-compat-headers kdelibs4-dev kdebase-dev

Good Luck, and post results

---

### Post by banadushi on 2006-01-07
The error will actually be above the line saying:
```

collect2: ld returned 1 exit status

```

This means that the linker (ld) did not exit successfully.  Most of the time this is because it cannot find a required symbol in any of the availible libraries it is told to link against.  This should all be the lines aboce the 'collect2' line.

Have a good one!

Jason

---


---
title: "kde installation problem"
date: 2005-06-06
forum: Absolute Beginner Talk
---

### Post by heart_reaver on 2005-06-06
](*,) 

i have tried to install kde library  kdelibs-3.4.1 form its source file it then ask for aRts 1.1 then i search for it and found rpm. by using alien i convert it.


after compiiling i am getting :::::::::::::



checking for aRts-1.1... ./configure: line 41035: cd: /usr/local/kde: No such fi le or directory
configure: error: aRts 1.1 not installed in the same prefix as KDE!
Please reinstall aRts in the same prefix as KDE, different prefixes are not
supported right now.

(kdelibs prefix is /usr/local/kde, aRts prefix is /usr)



 :???:

---

### Post by tread on 2005-06-06
Ok, my reply doesnt exactly answer your question - why are you trying to compile kdelibs? You can download kde or any kde utility using synaptic, this will handle all dependencies etc. If you want to compile your own kde application, you can download kdelibs-dev and then compile your code.

---


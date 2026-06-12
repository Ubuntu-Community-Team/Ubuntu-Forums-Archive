---
title: "i need a lil help"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by shinobininja on 2007-06-08
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.

---

### Post by Rotaj on 2007-06-08
The information you left is a little vague.
What were you trying to do or opening when this happened?

---

### Post by shinobininja on 2007-06-08
no i had a power surg and this happen but i dont kno wat i need to do

---

### Post by goodtimetribe on 2007-06-08
1.```
sudo aptitude remove virtualbox
```

2. ```
sudo apt-get install virtualbox
```

seems related to virtualbox... uninstall it and reinstall it should take care of it for ya, unless the package virtualbox doesn't exist.

---

### Post by rfurman24 on 2007-06-08
I am not real sure can you try to reinstall the virtualbox package in syanptic?

---

### Post by shinobininja on 2007-06-08
i still can do anything i uninstalled it but it wont let me reinstall it 'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

---

### Post by bapoumba on 2007-06-09
Please try:
```
dpkg --remove --force-remove-reinstreq virtualbox
```

---


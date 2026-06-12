---
title: "[SOLVED] Synaptic Problem"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by xdarkgokux on 2007-10-07
I get this error when i tried to install Virtual box
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'
I looked and tried the dpg or w/e thing.. plz help, i just want it out. i dont want to install it anymre

---

### Post by smartboyathome on 2007-10-07
That error usually comes up when the repos have changed. Just press the "reload" button in synaptic, and you should be good to go.

---

### Post by xdarkgokux on 2007-10-07
i do that and i get this E: 
The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by xdarkgokux on 2007-10-07
i just want to remove it plz help

---

### Post by xdarkgokux on 2007-10-07
anybody?

---

### Post by mysticrider92 on 2007-10-07
Try opening a terminal and typing 

> sudo apt-get install -f That sometimes helps, if not post back, with any errors.

---

### Post by xdarkgokux on 2007-10-07
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
 says the same thing

---

### Post by xdarkgokux on 2007-10-07
nvm, i got it.. i had to go to root( sudo su) and then put this in 
dpkg --remove --force-remove-reinstreq virtualbox
thx for the help anyway

---


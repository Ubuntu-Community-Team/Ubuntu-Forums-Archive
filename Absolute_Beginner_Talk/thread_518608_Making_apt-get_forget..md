---
title: "Making apt-get forget."
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-08-06
I recently forced-installed a .deb and now the update manager thingie is giving me errors.

When I run "sudo apt-get install -f" which is instructed by the error message, it asks me to remove the program.

This program runs fine even though the dependencies were not satisfiable, how can I make apt forget that the program exists (if possible)?

---

### Post by 505 on 2007-08-06
Just uninstall the program, and reinstall it again. Then all dependecies will be downloaded again. If you simply use 'apt-get remove' config files etc. will not be removed.

---

### Post by Kitsun on 2007-08-06
But it wont download the dependencies, I think the program wants a beta version or something, but it runs fine without the correct version when I force install it.

I just want to install it without Synaptic and its friends knowing so it doesn't cry every time I install an update or a new program.

---

### Post by alienexplorers on 2007-08-06
Unload the program.  Reload it and see what dependencies are missing.  Unload the program again.  Now load the missing dependencies using apt-get.  Now reload the program and it should recognize the dependencies.

---


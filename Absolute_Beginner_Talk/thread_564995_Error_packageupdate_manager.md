---
title: "Error package/update manager"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by XulluX on 2007-10-01
I am unable to do anything within the update manager or the package manager i get the following error messages:

Update manager:
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package vmwareworkstation needs to be reinstalled, but I can't find an archive for it.'

package manager:

E: The package vmwareworkstation needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I have tried removing the package though terminal, as well as manually deleting all the files using search.   

can anyone point me to my next step?

---

### Post by Pumalite on 2007-10-01
Try:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by XulluX on 2007-10-02
Thank you very much every things seems to be working. I love the response rate on this site. Most forums take forever and by the time that someone gets around to answering you have figured it out.

---

### Post by Pumalite on 2007-10-02
You are welcome. Good luck.

---

### Post by neurostu on 2008-03-31
Thank you so much for this thread! Man forums are great!

---


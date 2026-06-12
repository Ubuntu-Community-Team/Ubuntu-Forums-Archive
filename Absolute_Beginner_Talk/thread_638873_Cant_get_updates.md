---
title: "Cant get updates"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-12-12
When i try and get updates, it says they are 0 kb in size and it akso says This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.  But it's not running, also says cant get eclusive lock..What does all this mean?

---

### Post by wpshooter on 2007-12-12
Try rebooting your computer and then go into software sources, make sure all of the proper things are checked, then exit the diagonal and click on reload, if prompted, and then see if you can't get your updates.

---

### Post by sports fan Matt on 2007-12-12
I actually tried that and the same error appeared even after i rebooted the pc..very wierd!....

---

### Post by Majorix on 2007-12-12
You might have to delete some files from your /var folder, although I don't know which ones. /var contents are used by applications for storing data that changes during uptime, and Synaptic stores its data somewhere inside it too. Try looking inside and backup the suspicious files, then remove them. Finally try running Synaptic again.

---

### Post by skymera on 2007-12-12
your sources are Breezy.

i think updates stopped for breezy now =S

you posted a thread earlier but you never got ack to it

---


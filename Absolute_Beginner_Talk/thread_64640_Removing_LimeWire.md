---
title: "Removing LimeWire"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-09-11
I installed LimeWire using the instructions here: [http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

However, I wish to uninstall it now and cannot do so.  I have tried sudo apt-get remove limewire, but that didn't work.

Any suggestions?

Thanks for your help.

---

### Post by seiflotfy on 2005-09-11
try removing it through synaptic
open it and look for limewire !!!!

---

### Post by krusbjorn on 2005-09-11
[QUOTE=apmcavoy]I installed LimeWire using the instructions here: [http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

However, I wish to uninstall it now and cannot do so.  I have tried sudo apt-get remove limewire, but that didn't work.

Any suggestions?

Thanks for your help.[/QUOTE]

sudo rm -drf /opt/LimeWire

Edit: if you want to remove the configuration files, also:
rm -r ~/.limewire

---

### Post by amcavoy on 2005-09-11
That worked.  Thank you.  However, I also removed the Kubuntu Desktop Environment, and now have tons of broken icons (including that from LimeWire).  I can remove some manually, but is there a way to clean all of these leftover icons up?

Thanks again.

---


---
title: "Dependencies uninstalled with Synaptic?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-02-17
If I uninstall an app that was installed with Synaptic, do all of the dependencies get uninstalled also? I noticed that apptitude did this, but did not notice it with Synaptic. Is it just automated with Synaptic?

---

### Post by pvdg on 2007-02-17
No they don't. Aptitude is the the only tool that does it, AFAIK. Synaptic, however, keeps a record of all packages installed, upgraded and uninstalled: from the application menu, File>History.

---

### Post by mcduck on 2007-02-18
In Edgy apt-get also has 'autoremove' function (also available from Synaptic' that tries to detect packages installed as dependencies.. Combine that with deborphan and you can get very good results..

In Synaptic, look at the Status/Installed (auto removable). 

(I've had some serious troubles with aptitude, so I rather stick with apt-get and tools that it provides)

---


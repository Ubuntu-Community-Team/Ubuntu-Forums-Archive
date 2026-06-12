---
title: "synaptic - removal or complete removal?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-03-19
I've uninstalled an app for the first time, using Synaptic, and I see there's a choice of "removal" or "complete removal". What's the difference between these two options? I'm thinking it may be to do with extra packages that were installed so that the selected program could run.

---

### Post by Najand on 2007-03-19
According to the synaptic documentation:
> Debian only: To remove all files related to the package
				choose Mark for
				Complete Removal instead of 
				Mark for Removal.
I think completely removes all configurations and dependencies better than removal

---

### Post by garybrlow on 2007-03-19
Ordinary removal is equivalent to "sudo apt-get remove application" using terminal. It removes the software but preserves the configurations files. On your next installation of the same software or a newer version the configuration files will be reused.

Complete removal is equivalent to "sudo apt-get remove --purge application" using terminal. It removes the software and erases the configurations files as well.


Cheers!!!


GaryBrlow :biggrin:

---


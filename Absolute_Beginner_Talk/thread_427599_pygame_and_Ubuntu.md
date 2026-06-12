---
title: "pygame and Ubuntu"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by jcoggins on 2007-04-29
I cannot find the pygame module for python listed in any of the repositories.  Where can I find it?

Jason

---

### Post by Jeff24K on 2007-04-29
It's in "Universe".

Edit your /etc/apt/sources.lis and read the #comments, or enable the Universe repository in System > Administration > Software Sources, or enable it from Synaptic via Settings > Repositories. Then open Synaptic and "Reload" or invoke a 'sudo apt-get update' in a terminal. 

PyGame should show up as 'python-pygame'

---


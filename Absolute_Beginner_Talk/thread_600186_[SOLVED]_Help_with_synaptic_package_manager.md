---
title: "[SOLVED] Help with synaptic package manager"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2007-11-02
i have been trying to download programs for the past like 3 months now, and i cant figure it out. 
i have read alot about how, but nothing seems to work. 

but what i need help with is opening the synaptic package manager.
when i try it just says:

"An Error Occurred
the following details are provided

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

thats all i get. 

please help

---

### Post by Maestro23 on 2007-11-02
> **dylondadank said:**
> i have been trying to download programs for the past like 3 months now, and i cant figure it out. 
i have read alot about how, but nothing seems to work. 

but what i need help with is opening the synaptic package manager.
when i try it just says:

"An Error Occurred
the following details are provided

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

thats all i get. 

please help

In a terminal, run the following 3 commands.

> sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade

Post back the results.

---

### Post by dylondadank on 2007-11-02
awesome, the synaptic package manager is now open
what programs are needed to be downloaded in order to install .exe files

---

### Post by Maestro23 on 2007-11-02
> **dylondadank said:**
> awesome, the synaptic package manager is now open
what programs are needed to be downloaded in order to install .exe files

Good deal. :smile:
Linux does not use .exe files.  If you have Windows programs, you can look at running them 3 ways:

Wine: [http://www.winehq.org/](http://www.winehq.org/)

Or running Windows virtually with something like virtual box: [http://www.virtualbox.org/](http://www.virtualbox.org/)

Or dual-boot with XP.  This is what I do because I'm a heavy gamer.:)

Installing Software in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (Other good stuff)

---

### Post by dylondadank on 2007-11-02
thank you
is there a shortcut to downloading limewire?

---

### Post by Maestro23 on 2007-11-02
> **dylondadank said:**
> thank you
is there a shortcut to downloading limewire?

No prob man.

There's Frostwire for Linux: [http://www.frostwire.com/](http://www.frostwire.com/)

---

### Post by dylondadank on 2007-11-02
> **Maestro23 said:**
> No prob man.

There's Frostwire for Linux: [http://www.frostwire.com/](http://www.frostwire.com/)

thank you!

---


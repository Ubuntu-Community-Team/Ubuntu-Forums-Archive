---
title: "How to uninstall sopcast?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by seamustry on 2008-03-01
I installed a .deb for sopcast but it's not working so i need to remove it. how do i remove this program since it's not in synaptic or in add/remove?

thanks

---

### Post by neurostu on 2008-03-01
type
```

sudo dpkg -r <package name>

```

The exact package name might be hard to get right the first time... but keep trying

---

### Post by seamustry on 2008-03-01
how do i find out the name of the package?

---

### Post by wolfen69 on 2008-03-01
try
```
sudo apt-get remove sopcast
```

---

### Post by seamustry on 2008-03-01
doesn't work...it's called gsopcast but i tried that name and that doesn't work either. is there a list of installed packages, no matter how they were installed that i can see?

thanks

---

### Post by samwyse on 2008-03-01
Are you sure it's installed?

---

### Post by PeterJS on 2008-03-01
You could start up synaptic and search for sopcast. If it's installed anywhere that should find it.

---

### Post by neurostu on 2008-03-01
try moving to the directory where you had the deb file. then try sudo dpkg -r <name of debfile>

---

### Post by tbugge on 2008-03-19
> **seamustry said:**
> I installed a .deb for sopcast but it's not working so i need to remove it. how do i remove this program since it's not in synaptic or in add/remove?

thanks

i have had the same problem as you but then i saw this post and tried some of the suggestions in here.. i went to the terminal and typed the following: sudo dpkg -r GTK-sopcast

of course i dont know if you have the same package as me but its worth a shot!
i hope it will do the job

tell me if it works.. :)

---

### Post by ryukent on 2008-03-20
Not working? What version did you use? .... Is it a GUI client not working or the sopcast core? Also how did you install it?? From a deb or from a tar file??

---


---
title: "RPM to DEB"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by DoeRayMe on 2005-09-20
i can successfully get into the directory via the terminal but when i do the sudo sh intel.rpm command, it says the file doesnt exists, even tried typing the total path, but doesnt help

thanks in advance

---

### Post by mlomker on 2005-09-20
You can't install RPM's on debian systems...those packages are made for Redhat systems.  You can try converting it into a .deb package but the results aren't always perfect.

```

sudo apt-get install alien
alien -d intel.rpm
sudo dpkg -i intel.deb  (or whatever alien names the file...it'll tell you)

```

---

### Post by Perfect Storm on 2005-09-20
I think alien is installed by default.

---

### Post by mlomker on 2005-09-20
[QUOTE=Artificial Intelligence]I think alien is installed by default.[/QUOTE]

It is on 32-bit systems.  You'll notice what I'm running below.   :-P

---


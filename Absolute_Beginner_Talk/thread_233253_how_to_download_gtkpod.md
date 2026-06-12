---
title: "how to download gtkpod?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by DillPill on 2006-08-09
its not found in synaptic anymore, how else can i download it?

---

### Post by cstudent on 2006-08-09
Do you have all the repositories enabled?

---

### Post by DillPill on 2006-08-09
maybe i dont, how would i manage to put them on

---

### Post by cstudent on 2006-08-09
Go to the System menu (assuming you are using Gnome) and then Administration, then Software Properties. Enter your password when asked. Then check all the boxes down the list. You could also open Synaptic and select the Repositories menu and do the same thing. You'll want to Reload your packages list. Then do a search in Synaptic for gtkpod. It's there. I use it.

---

### Post by DillPill on 2006-08-09
i only have one one channel and thats getautomatix.com..should i add others to be able to download gtkpod?

---

### Post by cstudent on 2006-08-09
Open a terminal windows (Applications Menu > Accessories > Terminal) and enter the following:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak.bad

```
```

gksudo gedit /etc/apt/sources.list

```

Cut and paste the following sources.list into the blank page.

```

####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu dapper-backports main
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu dapper-backports universe
deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

```


Save the file and close the editor.

```

sudo apt-get update

```

After it gets done updating.

```

sudo aptitude install gtkpod

```


That should get you where you want to be. :)


cstudent

---


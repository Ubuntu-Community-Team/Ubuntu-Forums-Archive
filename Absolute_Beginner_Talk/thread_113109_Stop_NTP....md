---
title: "Stop NTP..."
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by nubuntux on 2006-01-05
Please help me how to Stop ntp from synchronizing at start-up? and how do i stop/start running services in command line? like for example in red hat it has "chkconfig" Thanks and happy new year!

---

### Post by loupy on 2006-01-05
You can either remove ntpdate from synaptic or you can run sysv-rc-conf (not installed by default) and deselect ntpdate.

There are probably other ways of doing it - but I'm a noob and these are the only 2 ways I know of doing it.

---

### Post by nubuntux on 2006-01-06
thanks! ill try...

---

### Post by Gray. on 2006-01-06
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
then remove the [X] from all entries in the ntpdate row then press q to update it.
Also I think you can disable it from the System > Administration > Services, though I aint in Gnome right now sorry.

---


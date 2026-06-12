---
title: "synaptic package manager kept crashing"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by rsun on 2007-02-03
After installing gstreamer0.10-pitfdll, the Synaptic manager kept crashing? I rebooted, shutdown the system, still could not get it to run. Please help!!

---

### Post by Spr0k3t on 2007-02-03
At the terminal:

$ sudo apt-get remove gstreamer0.10-pitfdll

This should remove the package for you and get you back into Synaptic.

---

### Post by rsun on 2007-02-03
now i get an error 
Segmentation faulty tree... 0%

---

### Post by taurus on 2007-02-03
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by rsun on 2007-02-03
results after running the commands update and upgrade

Reading package lists... Done
Segmentation faulty tree... 0%

------

---

### Post by taurus on 2007-02-03
How about

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```
And if you still get the same error message, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by rsun on 2007-02-03
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.



# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiversedeb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) dapper-commercial main
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
------

---

### Post by taurus on 2007-02-03
That's all there is for /etc/apt/sources.list!  Looks like you need to add a few more...

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by rsun on 2007-02-03
Great! :) 
SPM is running again after the update.
What went wrong?
Should I remove gstreamer0.10-pitfdll?

---


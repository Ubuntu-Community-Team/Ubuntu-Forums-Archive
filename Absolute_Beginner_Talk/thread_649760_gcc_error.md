---
title: "gcc error"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by psergiu on 2007-12-25
i got the following error when installing asterisk

checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

what's wrong??(on slack i installed the same asterisk with no problems)

---

### Post by taurus on 2007-12-25
You need the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by psergiu on 2007-12-25
sudo apt-get install build-essential does not work:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@psu-desktop:/home/psu/Desktop/asterisk-1.4.14# sudo apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@psu-desktop:/home/psu/Desktop/asterisk-1.4.14# sudo apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by taurus on 2007-12-25
Do you have synaptic or Add/Remove running?  You need to close them if you have them open before you run those two commands from a terminal.

---

### Post by LaRoza on 2007-12-25
Close any applications that are used for installing software. The Update Manager, Synaptic, Add/Remove and other commands can do this.

---

### Post by SOULRiDER on 2007-12-25
If after closing all applications youre still getting that error, type this in a termina
```
sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
```

---


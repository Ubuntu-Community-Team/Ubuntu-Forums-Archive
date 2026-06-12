---
title: "error while downloading packages"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by nate_nightroad on 2007-06-17
hi, today when i was downloading packages using add/remove applications, my internet connection was disconnected...but when i reconnect back and download the same packages again, an error occurs saying that the packages i want was unavailable....please advice.....

thanks......

---

### Post by meborc on 2007-06-17
to fix a broken install try the following things:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
```the last one beeing the most powerful :) it will see what installation is broken, look for dependencies, download and install all...

report back if problems still

---

### Post by nate_nightroad on 2007-06-17
the problem still presist....

the error reads:

some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?
no     yes

---

### Post by meborc on 2007-06-17
have you changed your sources list file?

this is strange...

---

### Post by nate_nightroad on 2007-06-17
i changed the sources list and it works....thanks

---


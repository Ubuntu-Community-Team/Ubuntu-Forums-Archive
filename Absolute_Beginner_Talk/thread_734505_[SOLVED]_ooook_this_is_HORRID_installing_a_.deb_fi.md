---
title: "[SOLVED] ooook this is HORRID: installing a .deb file and running into errors"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-03-24
This is really starting to make me angry I downloaded the .deb for Frostwire but whenver I tell gdebi to install the package it keeps telling me another thing such as synaptic is running, but I double checked and nothing else is running 


please help... I was installing another deb from the web but it wouldn't fully download or shut off so I restarted the comp.... what can I do?

---

### Post by joshrobinson on 2008-03-24
you sure your update manager etc isnt running? you can restart your computer and try again, maybe synaptic or the update manager is hung up and still running although its not open

---

### Post by -gabe-noob- on 2008-03-24
already tried rebooting 'cause Gdebi was held up

---

### Post by neurostu on 2008-03-24
Can you post the exact error message?

---

### Post by joshrobinson on 2008-03-24
can you post the output of you doing it manually in the terminal?
make sure you run it in the directory of the .deb file

```
 sudo dpkg -i packagename.deb
```

---

### Post by -gabe-noob- on 2008-03-24
Its the typical error:

Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'update manager'

and in terminal I get 

gabe@gabe-laptop:~$  sudo dpkg -i frostfire
[sudo] password for gabe:
dpkg: error processing frostfire (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 frostfire
gabe@gabe-laptop:~$

---

### Post by Joeb454 on 2008-03-24
Also you could try running ```
sudo dpkg --configure -a
``` before trying to install the .deb

This should fix any broken packages, and any half-downloaded packages too :)

---

### Post by -gabe-noob- on 2008-03-24
hah that last code SHOULD do it 'cause I'm thinking its the half downloaded package that is screwing things up

---

### Post by -gabe-noob- on 2008-03-24
worked, thanks

---

### Post by NullHead on 2008-03-24
Try ```
sudo apt-get install -f
```

EDIT: Ok glad you got it working ;) I posted to late :P

---


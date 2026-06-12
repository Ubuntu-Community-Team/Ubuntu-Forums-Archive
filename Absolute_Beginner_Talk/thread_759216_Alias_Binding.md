---
title: "Alias Binding ?"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Gripp on 2008-04-18
recently I added an alias 
alias usb='sudo /etc/init.d/bluetooth restart'
and it worked, at least i thought...
but then the next time my mouse and keyboard dropped out it didn't recognize the usb command....

not sure if it was that i had closed that terminal session, or maybe that my sudo had expired... but how do i get it to work?


edit: i just tested, and it seems to loose the alias after a restart the terminal session - any way to fix?

---

### Post by felicity on 2008-04-18
I append my alias' to the end of the .bashrc file in my home folder.

---

### Post by george9233 on 2008-04-18
After adding them to ~/.bashrc you need to source it by```
source ~/.bashrc
```so you don't need to log out and log in again for them to take effect.

---

### Post by Gripp on 2008-05-01
nice.
thanks

now is there a way that i can get it to automatically input the PW for the sudo in this case?

really i think i would just like to create a desktop icon that i click and it runs everything because often my mouse still works but keyboard doesn't

---


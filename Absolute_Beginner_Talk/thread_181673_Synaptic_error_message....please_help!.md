---
title: "Synaptic error message....please help!"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-05-24
hey guys

i`m getting an error message in synaptic which has been bugging me for a while, it happens when i try to remove the package lilypond-data.

here is the error message;

E: lilypond-data: subprocess post-removal script returned error exit status 1


i`ve tried a forced removal but my terminal command knowledge isnt great....help me!!! (pretty please)

i want rid of it as i have no use for it but it doesnt seem to want to go anywhere

cheers 

DK

---

### Post by daschl on 2006-05-24
try

```

$ sudo apt-get remove lilypond-data

```

if there is any further information about the package and why it couldn't be deleted please post it here

thanks!

---


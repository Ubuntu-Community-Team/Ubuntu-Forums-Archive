---
title: "Update"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by helrumyc1 on 2006-10-30
2 things, i just installed auntomatix, and now i have 2 problems that are ticking me off now

update manager will no longer open, it goes on for a second and closes and i cant run dynaptic package manager anymore, and when i try to edit the repositories, it just gives me error messages. Like i said everything ran fine before automatix, so if someone has a solution to this, please respond ASAP, thanks

---

### Post by bulldog on 2006-10-30
> **helrumyc1 said:**
> 2 things, i just installed auntomatix, and now i have 2 problems that are ticking me off now

update manager will no longer open, it goes on for a second and closes and i cant run dynaptic package manager anymore, and when i try to edit the repositories, it just gives me error messages. Like i said everything ran fine before automatix, so if someone has a solution to this, please respond ASAP, thanks

Try in your terminal ```
sudo aptitude remove automatix2
```

---

### Post by helrumyc1 on 2006-10-30
sudo aptitude remove automatix2
E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
E: The list of sources could not be read.

nope

---

### Post by bulldog on 2006-10-30
Where is your sources.list?

What if you type in your terminal```
gedit /etc/apt/sources.list
```

Do you get your sources.list?

---

### Post by helrumyc1 on 2006-10-30
blank page, i dont know what or why its moved, i didnt touch it it was stupid automatix or some f-ing crap, ive had this installed for one day, i havent used ubuntu in over a year, so i dont even know why this is happening

---

### Post by helrumyc1 on 2006-10-30
nevermind, i just reversed what automatix did and it put the sources back, everything should run fine now, thanks for the help though

---


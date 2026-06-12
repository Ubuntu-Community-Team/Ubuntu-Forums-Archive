---
title: "installing with apt-get"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by hnaamyilkemku on 2006-10-29
i can't install naim or 3ddesktop:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 3ddesktop

and

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package naim

why?

---

### Post by jd65pl on 2006-10-29
did you do the command below first?
```
sudo atp-get update
```

It is possible that there is too much load on the servers right now. Have you tried installing via synaptic?

---

### Post by pdub on 2006-10-29
You may need to add repositories:

Follow these instructions for Dapper:

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Follow these for Edgy:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

You can type sudo aptitude search naim

and

sudo aptitude search 3ddesktop 

to see if they are available. They are on my Edgy install using the above repositories.

---

### Post by hnaamyilkemku on 2006-10-29
thank you very much for the prompt responses!

---


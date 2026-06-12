---
title: "run program at boot"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by brdohman on 2008-03-29
I have a .jar file that I would like to have run at startup of an Ubuntu install.  Is there a way I can have it run automatically on boot?

Thanks

---

### Post by Inxsible on 2008-03-29
do you mean during the installation of the Ubuntu OS ?

if you mean you want to run that jar file everytime you boot into Ubuntu, then you need to add the command to run it under the Startup Programs in the Session menu

System>>Preferences>>Session
The command would be ```
java /path to jar files main class
```

---


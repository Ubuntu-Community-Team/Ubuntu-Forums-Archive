---
title: "RPM Files"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2006-01-30
I have a few apps like Snort 2.4 I would like to install but they are .rpm.

Is there a plugin or application that for Breezy that will open these files?

Thanks

Seek

---

### Post by Klaidas on 2006-01-30
Yes, you can convert RPM to DEB using alien (search for and install "alien" using Synaptic)

The comman will be
```
 sudo alien file.rpm 
```

Woot, I'm finally the first one to answer :)

---

### Post by lreyes6 on 2006-01-30
jajajajajaja thats the joy of helping people 

just a thing... if you convert the file from RPM to DEB you should see the dependencies of your original package such as java flash or something... because you can install the deb file but if something is absent the program wouldn't work

---

### Post by seekyrr on 2006-01-30
Worked great..Ty!

Seek

---


---
title: "Java runtime - Installed but dont work"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Dimicus on 2007-04-24
Hi guys, appreciate some answere here ;)

I have installed java runtime but it dont seem to work.

i attached print screen that for me provs that it's installed but dont work :)


Please advise me what im doing wrong. 

/Cheers
Dimicus

---

### Post by Sef on 2007-04-24
Go back to Add/Remove and uncheck Sun Java 5.0.  Leave Sun Java 6.0 on there by itself.

---

### Post by raja on 2007-04-24
I think you need the plugin.
```
sudo aptitude install sun-java5-plugin
```

---

### Post by crav on 2007-04-24
Are you using the right version of Java? This happened to me, I had installed a newer version, but I wasn't actually using it. This worked for me to change versions
```
sudo update-alternatives --config java
```

---

### Post by Dimicus on 2007-04-25
Thanx guys for good tips. what made it work was to install the plugin. Wierd i read that the plugin was installed if you install the runtime ? :) 


funny thing is that i had both ver 5 and 6 installed so decided to remove ver 6 becasue it dont seem to work anyway. i use synaptic to remove it and then i erased both as i thought. it should be uninstalled now but it still works in mozilla ? 

when i do sudo update-alternatives --config java
i dont get any hit. 

well im glad it work but it should not right ?. 

btw Sef: it never worked with Sun Java 6.0 by itself. but worked with sun java 5. 

Cheer
/Dimicus

---

### Post by Dimicus on 2007-04-25
Sorry was a restart of computer that was needed to realy uninstall the plugin.

everything works as it should now. thanx alot for the help.

---


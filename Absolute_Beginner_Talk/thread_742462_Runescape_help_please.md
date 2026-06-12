---
title: "Runescape help please"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by patrickm918 on 2008-04-01
I have tried installing java (all versions) and nothing happens what am I doing wrong can someone list step by step how to get java up and running so I can play. Would be greatly appreciated thanks.

---

### Post by patrickm918 on 2008-04-01
please help

---

### Post by markekeller on 2008-04-01
Have a look at these two links:

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

If you install the *sun-java6-plugin* package, it ought to work in Firefox.  The second of the two links explains what is necessary for other browsers.  Do you need help on how to install packages, too, or have you got that part figured out?

---

### Post by patrickm918 on 2008-04-05
I am still very confused not enough information can someone else please help??

---

### Post by Joeb454 on 2008-04-05
From a terminal (Applications>Accessories>Terminal)

Try running ```
sudo aptitude update
sudo aptitude install ubuntu-restricted-extras
```

One line at a time. And see if it works then :)

---

### Post by patrickm918 on 2008-04-05
for the first one when i ran it it came up with this error


Fetched 3B in 0s (4B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

What should i do continue to run the second one???

---

### Post by Joeb454 on 2008-04-05
ok in the terminal again, run ```
sudo dpkg --configure -a
``` and when that has finished, try and run the commands I posted originally :)

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Or just go to add/remove programs, install Sun Java stuff.

---

### Post by Joeb454 on 2008-04-05
As far as I'm aware, dpkg will still need to be fixed to use Add/Remove :)

---

### Post by I_R_LEENUCKS_MAN on 2008-04-05
Yepyep, if dpkg is broken.

---

### Post by patrickm918 on 2008-04-05
yea hello folks I did everything you said and then i tried loading the runescape page and I still come up with a message that says error loading applet 


Any suggestions on what to do??

---

### Post by patrickm918 on 2008-04-05
well i have sun java 6 on my computer but it will not work in the web browser any ideas???

---

### Post by Tyke91 on 2008-04-05
sometimes restarting helps... did you?

---

### Post by mivo on 2008-04-05
I'm not familiar with Runescape, but you mentioned your web browser. Could the problem be that you are using a 64-bit Ubuntu version? if so, you'll need to set up a second, 32-bit browser for the Java browser plugins to work (and for Java web start). 

Here's a good tutorial by Kilz: [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537) Note that this is only needed if you have a 64-bit system.

---

### Post by patrickm918 on 2008-04-06
well  how can i tell if i have a 64-bit system??

---

### Post by patrickm918 on 2008-04-06
where can i find one that works for ubuntu all the 32 bits are for other OS what to do what to do. I mean I tried to install them but there was an error that pops up that says there was an architectural error. Any ideas on what to do?:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by patrickm918 on 2008-04-06
can anyone help me??

---


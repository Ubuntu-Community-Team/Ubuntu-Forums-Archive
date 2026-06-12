---
title: "Error while installing"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Deathcab on 2006-07-04
On the rare occasion I figure out how to install something sometimes it give me this error.

[IMG]http://i6.tinypic.com/16m4ydu.png[/IMG]

I got it while I was installing automatix also. Help please?

---

### Post by Kilz on 2006-07-04
[QUOTE=Deathcab]On the rare occasion I figure out how to install something sometimes it give me this error.

[IMG]http://i6.tinypic.com/16m4ydu.png[/IMG]

I got it while I was installing automatix also. Help please?[/QUOTE]
I helped someone yesterday who had the same problem. They used automatrix to install java and it gave them the error. Here is what we did to get rid of it


I would open up synaptic , do a search for sun-java5, and remove those packages. or use this from automatrix removal page

```
sudo apt-get remove sun-java5*
```

Next I recommend it be replace by Blackdown java. Do a search for Blackdown, and install j2re1.4 or use the command

```
sudo apt-get install j2re1.4
```

---


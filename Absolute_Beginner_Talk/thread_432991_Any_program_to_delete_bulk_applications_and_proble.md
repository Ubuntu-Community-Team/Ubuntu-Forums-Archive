---
title: "Any program to delete bulk applications? and problem with frostwire..."
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by rausuar on 2007-05-04
Hi!

I would like to know if there is or are programs to run in ubuntu to eliminate bulk programs or files left behind by deleted applications or unused files... In windows I used Tune Up utilities, for example, but I dont know if in Ubuntu there is some app with a similar function.

I also want to ask if someone can help me, due that Im having problems when start up Frostwire, in the splash screen it frozes for 2 minutes and then starts loading ok.

I am using Ubuntu 7.04, P4, 512 RAM, latest JAVA release.

Thanks... - Raul

---

### Post by Cypher on 2007-05-04
To remove applications I use
```

sudo apt-get autoremove <package>

```
Some packages might leave their configuration files behind if you ever re-install and if I don't want these to hang around I do
```

dpkg --purge <package>

```

---


---
title: "Prolem with packeges"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by cursebg on 2007-04-04
i've installed a package and then i wanted to install another one but there was a problem with  the dependencies. so i unistalled the the problematic package and tried to install the dependable one(the another) and it keeps showing the problem with the dependency

pls,how can i install the package now?

---

### Post by taurus on 2007-04-04
What package do you want to install and what's the output of these commands?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Maestro23 on 2007-04-04
What were you trying to install?  Thru Synaptic(GUI) or Command line.  If command line, what commands did you use and what was the error.

---

### Post by cursebg on 2007-04-04
> **Maestro23 said:**
> What were you trying to install?  Thru Synaptic(GUI) or Command line.  If command line, what commands did you use and what was the error.

 Synaptic

---

### Post by cursebg on 2007-04-04
> **taurus said:**
> What package do you want to install and what's the output of these commands?

```
sudo aptitude update
sudo aptitude upgrade
```

it's pptp and i've got php-pcntl which is the pitfall, i've removed php-pcntl but the deb installer of the pptp shows me that the dependency is still active

---

### Post by cursebg on 2007-04-04
> **cursebg said:**
> it's pptp and i've got php-pcntl which is the pitfall, i've removed php-pcntl but the deb installer of the pptp shows me that the dependency is still active

i'll try the commads later coz i'm using the windows for accessing the internet, i need pptp to access the internet through Ubuntu

---

### Post by zvacet on 2007-04-04
If you want to remove dependecies
```
sudo apt-get autoremove
```
And if you  want to install somethng and be sure that dependencies will be installed too
```
sudo aptitude install program_name
```

---


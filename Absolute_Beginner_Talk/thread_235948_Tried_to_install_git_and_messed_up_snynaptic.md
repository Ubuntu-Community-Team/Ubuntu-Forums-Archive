---
title: "Tried to install git and messed up snynaptic"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2006-08-14
how do it uninstall it?

---

### Post by jasonpeinko on 2006-08-14
help please

---

### Post by jasonpeinko on 2006-08-14
please help i cant install anything from snaptic of apt

---

### Post by bruce89 on 2006-08-14
In what way is it messed up?

---

### Post by goatflyer on 2006-08-14
have you checked if your repositories list is damaged or not?  i.e. look at

/etc/apt/sources.list

If its empty or corrupt, restore it to default values (depends on your country) and synaptic should work again.

---

### Post by jasonpeinko on 2006-08-14
no it is not empty but how do you restore it?

---

### Post by bruce89 on 2006-08-14
> **jasonpeinko said:**
> no it is not empty but how do you restore it?

That's probably not the problem.  What happens when you run synaptic?

---

### Post by jasonpeinko on 2006-08-14
asks for password, then when it loads it says The following problems were found on your system: E: Type 'git' is no known on line 35 in source list /etc/atp/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem

---

### Post by jasonpeinko on 2006-08-14
I fixed it i just erased line 35 in the sources.list

---


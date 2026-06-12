---
title: "Envy"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-10
Hi when trying to install Envy on a fresh ubuntu studio i get this 
[[img]http://bildr.no/thumb/74482.jpeg[/img]](http://bildr.no/view/74482)
PLZ help

and when trying to install java i get this [[img]http://bildr.no/thumb/74483.jpeg[/img]](http://bildr.no/view/74483)

---

### Post by mikewhatever on 2007-06-10
Have you enabled Universe and Multiverse in Software Sources? A line in the second screenshot directly suggests it.

---

### Post by ajmannen on 2007-06-10
Umm... i have enabled everything that was on defult in synaptic, i think.

i can't find anny mutliuniverse things there but i can find some uiniverse

---

### Post by p_quarles on 2007-06-10
[COLOR=Black]The problem with the Java install is incorrect syntax. Try:
```
sudo apt-get install sun-java6-jdk
```

The terminal will then ask you for your password, and will install the package once you enter it. 
[/COLOR]

---

### Post by ajmannen on 2007-06-10
still the same problem "could not find packege bla bla bla"

---

### Post by mikewhatever on 2007-06-10
> **ajmannen said:**
> Umm... i have enabled everything that was on defult in synaptic, i think.

i can't find anny mutliuniverse things there but i can find some uiniverse

'Everything that was on default'? What are you talking about? Why enable something enabled by default? In Feisty, you'd go to System>Preferences>Software Sources, check the screenshot. If you can't find it, post the output of the following from the terminal
> cat /etc/apt/sources.list

---


---
title: "li|}rary help"
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-07-20
all the programs i downloaded need more li|}rarys that i dont have so where do i put put them after downloading?

---

### Post by TravisNewman on 2005-07-20
4 questions.

1. What programs have you downloaded?
2. What libraries do they need?
3. How are you installing things?
4. Why li|}raries instead of libraries? ;)

Most things are available in the apt repositories if you've added universe/multiverse, and even more are available with backports. See this link to find out how to add those repositories:
[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

In order to install things, either search for them in synaptic, which is in System -> Administration, or use apt-get at the terminal, ie "sudo apt-get install ****" where **** is the package you want.

---

### Post by black hole sun on 2005-07-21
Is your `b` key |}roken, Jason? :D

---

### Post by jasonpeinko on 2005-07-21
e><acily so, is the ><

i have
lives
nvu 
and others ut my dad keyoard keys are slowly dieing one y one i cant use shift anymore.

---

### Post by jasonpeinko on 2005-07-21
> **panickedthumb]4 questions.

1. What programs have you downloaded?
2. What libraries do they need?
3. How are you installing things?
4. Why li|}raries instead of libraries?  said:**
> http://www.ubuntuguide.org/#repositories[/url]

In order to install things, either search for them in synaptic, which is in System -> Administration, or use apt-get at the terminal, ie "sudo apt-get install ****" where **** is the package you want.

do i need internet my network is not set up yet and im using my dads comp.

---

### Post by black hole sun on 2005-07-21
[QUOTE=jasonpeinko]do i need internet my network is not set up yet and im using my dads comp.[/QUOTE]
 You need the internet, yes, and a new keyboard, because apt-get will not understand your, ahhm, "replacement letters".

---

### Post by TravisNewman on 2005-07-21
you CAN however browse through synaptic to get what you need. But yeah, those will need internet. Finding out the dependency tree can be a pain without the use of apt, but it's possible. You can try to install, grab the dependencies it complains about from packages.ubuntu.com, install those with dpkg -i, and then try again until you get it to work. But that's quite a pain like I said.

---

### Post by jasonpeinko on 2005-07-21
[QUOTE=black hole sun]You need the internet, yes, and a new keyboard, because apt-get will not understand your, ahhm, "replacement letters".[/QUOTE]
 no i dont need another key board i was using my dads comp last night DADS
mine has a working keyboard. but we have found that it is a virus on my dads comp.
k thx for the help

---


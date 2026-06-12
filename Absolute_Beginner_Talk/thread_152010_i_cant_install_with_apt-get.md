---
title: "i cant install with apt-get"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by jackss on 2006-03-29
hi, i think i ruin the sources.list because i cant install anything
, i get error when try to use apt-get
how can i fix that?

---

### Post by Princey on 2006-03-29
[QUOTE=jackss]hi, i think i ruin the sources.list because i cant install anything
, i get error when try to use apt-get
how can i fix that?[/QUOTE]

What is the exact error message are you getting? Can you post the error message that someone can provide you with some guidance?

---

### Post by jackss on 2006-03-29
for example when i try to install flash with sudo apt-get install flashplayer-mozilla
i get:
 sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  flashplayer-mozilla: Depends: gsfonts-x11 but it is not installable
E: Broken packages

---

### Post by aysiu on 2006-03-29
[QUOTE=jackss]hi, i think i ruin the sources.list because i cant install anything
, i get error when try to use apt-get
how can i fix that?[/QUOTE] Go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Mustard on 2006-03-29
[QUOTE=jackss]for example when i try to install flash with sudo apt-get install flashplayer-mozilla
i get:
 sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  flashplayer-mozilla: Depends: gsfonts-x11 but it is not installable
E: Broken packages[/QUOTE]

Visiting the link above from aysiu would be a good start.

What repositories have you been using in your sources.list?

---

### Post by mostwanted on 2006-03-29
apt-get is the most basic you can get. Synaptic is far better at solving dependencies.

---

### Post by Princey on 2006-03-29
[QUOTE=jackss]for example when i try to install flash with sudo apt-get install flashplayer-mozilla
i get:
 sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  flashplayer-mozilla: Depends: gsfonts-x11 but it is not installable
E: Broken packages[/QUOTE]


Try sudo apt-get -f install and see what happens. Most times it fixes the broken dependency problem.

---

### Post by aysiu on 2006-03-29
[QUOTE=mostwanted]apt-get is the most basic you can get. Synaptic is far better at solving dependencies.[/QUOTE] As far as I know, Synaptic is just a graphical front-end for apt-get.

---

### Post by meborc on 2006-03-29
[QUOTE=aysiu]As far as I know, Synaptic is just a graphical front-end for apt-get.[/QUOTE]

thats right... that is also why you can't run apt-get from terminal and synaptic at the same time... cuz they are the same thing ;)

---

### Post by mostwanted on 2006-03-29
[QUOTE=aysiu]As far as I know, Synaptic is just a graphical front-end for apt-get.[/QUOTE]

Not just. Synaptic and aptitude can solve dependency problems if any occur. Apt-get just tries to install the dependencies procedural style and if it meets any problems, it will back off in an instant.

There's a reason why some people recommend *aptitude install X* instead of *apt-get install X*.

---

### Post by catlett on 2006-03-29
Sorry to go off topic but,...Are apt-get, synaptic and aptitude all getting programs from the same resource? Are they just different ways to install the same cache or do they have seperate places to draw upon?

---

### Post by aysiu on 2006-03-29
[QUOTE=mostwanted]Not just. Synaptic and aptitude can solve dependency problems if any occur. Apt-get just tries to install the dependencies procedural style and if it meets any problems, it will back off in an instant.

There's a reason why some people recommend *aptitude install X* instead of *apt-get install X*.[/QUOTE] Can you explain a bit more about this? I know aptitude handles dependencies differently in the sense that it can "remember" what was installed with an application (to make uninstalling cleaner), but if a dependency is not available, what can aptitude do that apt-get can't? Aren't they both drawing on the same sources.list?

Also, it kind of make sense to back off if you hit problems. apt-get also has the option to use --force-yes, but I don't know if that's advisable.

---


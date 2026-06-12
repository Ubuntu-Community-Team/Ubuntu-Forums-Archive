---
title: "Error installing XGL"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by antharr on 2006-12-02
I get the following when trying to install the following components. 

keith@keith-desktop:~$ sudo apt-get install xserver-xgl compiz compiz-core compiz-gnome compiz-plugins libglitz1 libglitz-glx1
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-plugins: Depends: compiz-core (>= 0.0.13.54) but 0.0.13.38-0ubuntu3 is to be installed
                  Depends: csm (>= 0.5) but it is not installable
E: Broken packages

Any hints on how to get this right?

---

### Post by rooi on 2006-12-13
I'm getting this exact same error. Fresh install as of today for Kubuntu, with the same error when trying install XGL w/ Compiz... anyone else having this problem, or able to give any insight?

---

### Post by xander.helpdesk on 2006-12-13
](*,)  I was able to install xgl however my media players are not working properly also the xgl, maybe I miss-configured my video card, Did someone know how to configure again without using the xorg-xserver?

Please advise.

---

### Post by xander.helpdesk on 2006-12-13
> **antharr said:**
> I get the following when trying to install the following components. 

keith@keith-desktop:~$ sudo apt-get install xserver-xgl compiz compiz-core compiz-gnome compiz-plugins libglitz1 libglitz-glx1
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-plugins: Depends: compiz-core (>= 0.0.13.54) but 0.0.13.38-0ubuntu3 is to be installed
                  Depends: csm (>= 0.5) but it is not installable
E: Broken packages

Any hints on how to get this right?


Did you already installed the dependencies?:confused: 
compiz-plugins
compiz-core

---

### Post by peril blue on 2006-12-14
I'm gettin the same error, i don't know what is causing the problem. this is holding me back from eye candy.

i can't install 'compiz' because it depends on 'plugins' and plugins won't install because i get the non-installable error from up the first post. any suggesstions?

](*,) ](*,)

---

### Post by peril blue on 2006-12-14
btw, it says my compiz core, that i have installed, is 0.0.13.38 - a lower version than the installation is asking for...

---

### Post by rooi on 2006-12-14
I think that the real error is coming from "compiz-plugins" and the dependency on "csm", forgot to post my error before too, but its the exact same...

```
The following packages have unmet dependencies:
  compiz-plugins: Depends: compiz-core (>= 0.0.13.54) but 0.0.13.38-0ubuntu3 is to be installed
                  Depends: csm (>= 0.5) but it is not installable
E: Broken packages
```

---


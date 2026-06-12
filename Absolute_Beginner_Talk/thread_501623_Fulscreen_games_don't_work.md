---
title: "Fulscreen games don't work"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-07-15
I have a RV280 (Radeon 9200) ATi card, and it seems to have worked out of the box, except for full screen games. Am I missing some drivers or something? What can I do?

edit: same w/ games under Wine as well. windowed mode works fine though.

---

### Post by reset3x on 2007-07-15
> **FleetAdmiral74 said:**
> I have a RV280 (Radeon 9200) ATi card, and it seems to have worked out of the box, except for full screen games. Am I missing some drivers or something? What can I do?

edit: same w/ games under Wine as well. windowed mode works fine though.

Some games have an option for full screen.. Have you maybe overlooked that?

---

### Post by FleetAdmiral74 on 2007-07-15
Well most games are full screen by default, so as soon as I start it the screen wacks out, and flickers heavily.  Thus, I cannot get into the games options menu.

---

### Post by reset3x on 2007-07-15
Are you trying to play with compiz or beryl running? That can cause headaches... Otherwise it sounds like it may be a driver problem...

---

### Post by FleetAdmiral74 on 2007-07-15
No compiz or beryl. Hence me thinking it was a driver problem in my first post :)

---

### Post by Daveth on 2007-07-15
if it is an old driver problem, this

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

will help out.

---

### Post by reset3x on 2007-07-15
Go here : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and download/install Envy... This will install your ATI drivers and configure Xorg for you...

---

### Post by FleetAdmiral74 on 2007-07-16
Is Envy like Automatix?

---

### Post by reset3x on 2007-07-16
> **FleetAdmiral74 said:**
> Is Envy like Automatix?

Envy has a GUI and installs/uninstalls ATI and nVidia proprietary drivers... I've had bad experiences with Automatix myself....

---

### Post by FleetAdmiral74 on 2007-07-16
That is why I asked. I have heard to much about how Automatix can mess up your system, I did not want a program with that bad a rep. So I should be safe w/ envy?

is Envy in the repos?

---

### Post by reset3x on 2007-07-16
> **FleetAdmiral74 said:**
> That is why I asked. I have heard to much about how Automatix can mess up your system, I did not want a program with that bad a rep. So I should be safe w/ envy?

is Envy in the repos?

Envy works great... It will also work in text mode should you need to use it in recovery mode... Envy is not in the repo's... You can download it from the link above... It's a deb file... Just d/l and double click on the file and GDebi will open and install it... If you decide you don't like it you can uninstall easily through Synaptic.....

---

### Post by FleetAdmiral74 on 2007-07-16
Installed ok, went to the gui frontend to install the ATi driver automatically, got

---

### Post by reset3x on 2007-07-16
What card do you in fact have?

---

### Post by reset3x on 2007-07-16
OK here's the fix to get your system back... It looks like you're card isn't supported... [http://albertomilone.com/wordpress/?p=82](http://albertomilone.com/wordpress/?p=82) See 6.

---


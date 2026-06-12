---
title: "Can't use KDM theme manager"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by LostArt on 2007-05-13
So I have KDM theme manager, but it says I need to provide the root password to use it, but how am I supposed to do that is there is nowhere to type it in, all I want to do is change my theme??? 

To use Kdm I'm going to K menu > System Settings > Appearance > Kdm theme manager

---

### Post by Bachstelze on 2007-05-13
When you click on the "Administrator mode" butto, doesn't it prompt for your password ?

---

### Post by Nythain on 2007-05-13
in terminal run
kdesu kcontrol
and get to it from there

---

### Post by Nythain on 2007-05-13
> **HymnToLife said:**
> When you click on the "Administrator mode" butto, doesn't it prompt for your password ?
for some reason, when getting to it the way lostart is, there is no admistrator mode button... i just checked and rechecked, resized the window thinking it was hidden, maximized the window, the button just isnt there, but it is in the full kcontrol

---

### Post by Bachstelze on 2007-05-13
Once again, Ubuntu thinks it knows better and makes "improvements" that in fact break stuff...

---

### Post by Nythain on 2007-05-13
hehe... yeah... i learned a while back to rely more on the terminal and the actuall programs and not the ubuntu implementation (hope thats the word im looking for) of them

---

### Post by Bachstelze on 2007-05-13
Well, actually the KDM Theme Manager works very well in *any* other distro but Ubuntu's doesn't. No wonder many Ubuntu users don't like KDE with such a broken version in the repos...

---

### Post by LostArt on 2007-05-13
Umm trying it now thanks

---

### Post by LostArt on 2007-05-13
It only does it on the kde control centre window,and nothing else, what know

---

### Post by Nythain on 2007-05-13
go down to system administration-------> kdm theme manager
it should look like the one you were using before, except now you can install and remove anything you see fit... there shouldnt even be a button for administrator mode since you ran kcontrol with with the kdesu command and hopefully put in your password when asked

---

### Post by LostArt on 2007-05-13
ok I see what I was doing now thanks

---

### Post by LostArt on 2007-05-13
Wait, I'm not trying to install a splash screen, I want a whole screen, so I'm going to the appearence tab in the K control menu, but it is only changing the K control window, and not my whole desktop. Agh why can't it just be easy.

---

### Post by Happy_Man on 2007-05-13
delete...

---

### Post by blop on 2007-05-17
Thanks that terminal command solved my probs too...

kdesu kcontrol

---

### Post by Amazing_Ri on 2007-05-20
Thanks again.  I was fighting with that for a while now, and well, this worked like a charm.  It's a shame KDE seems to have little bugs like this, because the whole look and feel of it is what drew me away from XP.  the console still scares me a bit, so it's usually GUIs for me.

---

### Post by Jimmy Johnson on 2008-03-26
> **LostArt said:**
> So I have KDM theme manager, but it says I need to provide the root password to use it, but how am I supposed to do that is there is nowhere to type it in, all I want to do is change my theme??? 

To use Kdm I'm going to K menu > System Settings > Appearance > Kdm theme manager

I thought I would post in case I could help someone, Ubuntu's "kdmtheme" manager did not work for me, so while using Synaptic I completely removed it and downloaded "kcontrol-kdmtheme" from here: [http://kambing.ui.edu/ubuntu/pool/universe/k/kcontrol-kdmtheme/](http://kambing.ui.edu/ubuntu/pool/universe/k/kcontrol-kdmtheme/) if you have "kpackage" installed then all you need to do is click on the "kcontrol-kdmtheme" .deb file and kpackage will open with the deb file ready for you to install.

This worked for me, I hope it helps you.

---

### Post by Tenebrae on 2008-05-07
> **Jimmy Johnson said:**
> I thought I would post in case I could help someone, Ubuntu's "kdmtheme" manager did not work for me, so while using Synaptic I completely removed it and downloaded "kcontrol-kdmtheme" from here: [http://kambing.ui.edu/ubuntu/pool/universe/k/kcontrol-kdmtheme/](http://kambing.ui.edu/ubuntu/pool/universe/k/kcontrol-kdmtheme/) if you have "kpackage" installed then all you need to do is click on the "kcontrol-kdmtheme" .deb file and kpackage will open with the deb file ready for you to install.

This worked for me, I hope it helps you.

Oh, it surely DID help :-)
Thank you, I was about to give up on customising kdm.

---

### Post by provide on 2008-05-12
Thanks, Jimmy! Your solution allowed me to change KDM's theme. 

...which brings me to a couple of other questions (open to anyone in general):

1) I now know how to run kcontrol (run dialog ---> kcontrol) but why isn't it in the menu by default? 

2) What is the real difference between systemsettings (System Settings in the K Menu) and kcontrol?

3) Is it fair to ask why something as (I assume) simple as the login screen's theme manager doesn't work out of the box?

---

### Post by provide on 2008-05-12
Thanks, Jimmy! Your solution allowed me to change KDM's theme. 

...which brings me to a couple of other questions (open to anyone in general):

1) I now know how to run kcontrol (run dialog ---> kcontrol) but why isn't it in the menu by default? 

2) What is the real difference between systemsettings (System Settings in the K Menu) and kcontrol?

3) Is it fair to ask why something as (I assume) simple as the login screen's theme manager doesn't work out of the box?

---


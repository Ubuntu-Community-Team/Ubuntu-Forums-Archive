---
title: "OK where did synaptic go?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-11
Hi people how are you?
After having Ubuntu running with Gnome and Beryl with no problems, I had to switch machines. So now I'm on my good machine and thought I give Kubuntu 64bit a go.

Installed Kubuntu no problems. I got internet working but I cannot find Synaptic on the menu. KDE is so much different than Gnome. The menu is full of apps but I cannot find Synaptic Package Manager in order to install apps.

---

### Post by bone2006 on 2007-09-11
kubuntu doesn't have synaptic Package Manager if I'm not mistaken.  It has something else called Aptitude if I'm not mistaken.  Search for it and you can installed synaptic package manager from aptitude

---

### Post by DBStevens on 2007-09-11
Hit the nice K gear (start button) then in System.

---

### Post by jw5801 on 2007-09-11
Command line to the rescue!
```
kdesu synaptic
```
I think that's the graphical sudo for kde anyway. I use gnome so I actually have no idea where it is by default in the kde menu, but that command should get you into synaptic anyway! Unless kde uses a different package manager...?

EDIT: apparently it doesn't! So use:
```
sudo aptitude install synaptic
```if you would like it!

---

### Post by hyper_ch on 2007-09-11
Kubuntu comes with "Adept" but I tend to think it's worse than synaptic...

aptitude and apt-get are command line tools which I prefer to use and which are in all Ubuntu installs.

---

### Post by ROUBOS on 2007-09-11
this KDE is so different. Ubuntu makes things so much easier with the Synaptic Package Manager. 
In KDE under System I see the Adept Manager..

KDE is more graphical, but my  Gnome with Beryl was awesome... Gnome seems like a better way to go I think.

---

### Post by jw5801 on 2007-09-11
I also much prefer the command line package options.

And as for your first question, I'm feeling mighty alright, how about yourself? :p

---

### Post by DBStevens on 2007-09-11
You should also see synaptic under system in addition to adept .....

---

### Post by ROUBOS on 2007-09-11
no synaptic is no there. Looks like I'll have to install it.
But the adept manages seems to be working... will take some getting used to.
KDE is different. Is there a guide so I can setup my graphics card beryl and all?
ATI X1950 pro 512mb

And it keeps on poping up with this secure wallet thing when I enter passwords... what is it?

---

### Post by DBStevens on 2007-09-11
If synaptic isn't there it wasn't installed but it can be and it works just great.

That secure wallet is a applet that will manage passwords I used it a bit in the past, but I don't currently have it installed.

My actual system is a blended one, I can choose at startup.   I usually use xfce so I selected Xubuntu since they don't have any blended options :( .  I also spend a chunk of time in command line mode using several flavors of Red Hat.  I used to run SuSE here at the house, but Novell ticked me off, so I tried several distros and converted my system.

---

### Post by DBStevens on 2007-09-11
I can't speak to Beryl as it requires the use of a binary blob on my system to activate the graphic card features required.  There is probably a guide somewhere but I never had a need for it.

Such is the fate of those that want the source to play with ;) .

---

### Post by ROUBOS on 2007-09-11
Well I'm back, this time within Gnome.
I just did a re-install with Ubuntu 64. Got rid of Kubuntu. Good to be back to this simple light environment that just works :)

---

### Post by hyper_ch on 2007-09-11
> **ROUBOS said:**
> Good to be back to this simple light environment that just works :)
Xfce?

---

### Post by DBStevens on 2007-09-11
hyper_ch,

Shhhhh, don't go giving away secrets :) .

---

### Post by ROUBOS on 2007-09-12
Xfce must be cool. I used something similar in Unix, if I remember correctly it was "fvwm". When I did my Computer Science degree back in 1995 on Unix machines. We did all the C programming on Unix.
You got me thinking now. I should try to get back to that style of environment. Window$ has done a lot of damage to me ](*,)

---

### Post by hyper_ch on 2007-09-12
```

sudo aptitude install xubuntu-desktop

```

Very easily installed and ready for being tested ;)

---

### Post by ROUBOS on 2007-09-12
I installed it from Synaptic and when I log out of gnome and try to change a session, it's not there :/

---

### Post by ROUBOS on 2007-09-12
Isn't Xubuntu desktop like gnome? I installed xfce through synaptic.

EDT >> I installed it with the command you gave me. Cool it works now. I've seen Xubuntu before. It looks like a lighter version of gnome. Not like the screenshots I see of people using it. Anyway will have to google and customize it a little.

---


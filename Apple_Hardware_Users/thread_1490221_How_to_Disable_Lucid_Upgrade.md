---
title: "How to Disable Lucid Upgrade"
date: 2010-05-22
forum: Apple Hardware Users
---

### Post by philtro on 2010-05-22
Hi, I've just installed Kubuntu 9.10 on a friends powerbook g4 and it's running wonderfully.  I don't want to upgrade to Lucid, I tried it and it ran not so good on this computer.  How can I tell it to stop offering to upgrade to the next release?  (I only want the automatic upgrade notification to appear for normal upgrades and not include Lucid, or have Lucid option to appear at all).

thanks!  
p

---

### Post by philtro on 2010-05-22
Ok I figured it out, I had to install synaptic manager and it had more options, including the update to next release notice.

hope it helps someone else

---

### Post by philtro on 2010-05-22
> **philtro said:**
> Ok I figured it out, I had to install synaptic manager and it had more options, including the update to next release notice.

hope it helps someone else

Nevermind, this just told synaptic not to offer it, i'm still getting the update to lucid icon when the computer is rebooted :(

If anyone can help....

---

### Post by drs305 on 2010-05-22
You can also modify the settings via System, Administration, Update Manager. Click on settings and 'Updates' to get to the same screen you probably found in Synaptic. Of course, the 'express' way of getting to this screen is via System, Administration, Software Sources. In all of these, at the bottom are release upgrade options, including "never".

Edit: Kubuntu! Well, I'll have to check my VM when I return home tomorrow.

---

### Post by philtro on 2010-05-22
Thanks for the reply! 

I guess i'm just missing things on this Kubuntu ppc release; there's no update manager to open or software sources...I tried to find it in the repo but they're not making it so easy :D

Is there some way to do it from the terminal maybe or by editing a config file somewhere?

---

### Post by buntuLo on 2010-05-23
> **philtro said:**
> I guess i'm just missing things on this Kubuntu ppc release; there's no update manager to open or software sources...I tried to find it in the repo but they're not making it so easy :D
mmmm, same here: on Kubuntu 9.10 (KDE 4.3), in the settings of KPackageKit under Software Sources, there's plenty of options, but no one about distribution upgrades.
> **philtro said:**
> Is there some way to do it from the terminal maybe or by editing a config file somewhere?
the repository list is at:
```
sudo nano /etc/apt/sources.list
```but there's no obvious (to me) reference to distro upgrades..
any help?

---

### Post by drs305 on 2010-05-23
I checked my Kubuntu 9.10 VM and unfortunately had the same result. I couldn't find a "dist-upgrade" option to disable. So I'll have to let a Kubuntu expert come up with the solution - at least this will bump the thread.

---

### Post by LarsO on 2010-06-18
sudo nano /etc/update-manager/release-upgrades

then replace the 'normal' in Prompt=normal with 'never'

---

### Post by buntuLo on 2010-06-19
> **LarsO said:**
> sudo nano /etc/update-manager/release-upgrades
then replace the 'normal' in Prompt=normal with 'never'
thanks, Lars!

---


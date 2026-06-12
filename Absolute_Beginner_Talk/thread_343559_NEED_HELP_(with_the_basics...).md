---
title: "NEED HELP (with the basics...)"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by asusguy175 on 2007-01-21
i just installed my first linux system (edgy) and i need help with getting started,  my computer doesn't cooperate with the drivers, so i'm just leaving them at default, at least for now... but if someone could help me set up my wireless card (i am using a laptop) and make it active, that would be nice, if someone could help me out with WINE.... i need to figure that out too, including where to get it.... i see some other threads that mention it, but no direct download link or even the right website (i think) so if you can offer me any help at all PLEASE HELP;):confused::confused::confused:

---

### Post by zekopeko on 2007-01-21
for wine follow the instructions from this site: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

for various software use Synaptic Package Manager. It is in System > Administration.
other alternative is Add/Remove Programs from Applications Menu. This are selected programs so 
use synaptic for detailed search.

EDIT: for wireless somebody else will have to help you out. try searching google. search model and brand of your laptop and try do find out which wireless card you have. then try searching the forums for instructions on installing it.

---

### Post by Shatrat on 2007-01-21
Getting your hardware going depends on just what hardware you have.
Wireless cards are often a pain because the manufacturers don't support linux, but there are ways to get most of them working.
What kind of wireless card do you have? Manufacter and model number would be helpful. If you dont know, you might be able to find that info in the System -> Administration -> Device Manager

As for installing wine, just open up synaptic in the System -> Administration menu and search for it.
I believe it is in the default repositories, if it isnt you might have to add a new repository but check first.

---

### Post by Jeroen Vernooij on 2007-01-21
For wireless, i would recommend installing linux-restricted-modules, as it contains extra drivers.

If you are running gnome, paste this into terminal:
```
sudo apt-get install linux-restricted-modules-$(uname -r) network-manager-gnome
```


If you are running kde, paste this into terminal:
```
sudo apt-get install linux-restricted-modules-$(uname -r) network-manager-kde
```


Good luck
Jeroen

---

### Post by asusguy175 on 2007-01-21
i have an HP ze5300 laptop, so that might tell you what wireless card i have, and for wine, i can't seem to get it to work... every time it downloads, it fails and says: W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263 so basically, i still need to figure out how to get wireless and wine.... don't have either one yet..... oh, and i don't know which one i'm running whether i'm running GNOME, or KDE.... how do i tell?

---

### Post by Jeroen Vernooij on 2007-01-22
Well if you are seeing something like this you are running GNOME:
[http://shots.osdir.com/slideshows/751/5.gif](http://shots.osdir.com/slideshows/751/5.gif)


and something like this is KDE:
[http://shots.osdir.com/slideshows/752/5.gif](http://shots.osdir.com/slideshows/752/5.gif)

(you are probably running GNOME as it is default)

I could not find which wireless chipset you have, but maybe it will work with my terminal command.

---

### Post by Jeroen Vernooij on 2007-01-22
For Wine, you can also just browse to [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) and download the .deb and run it, I think. That's a lot easier than fooling around with repositories and associated GPG keys.

---

### Post by jvc26 on 2007-01-22
> **asusguy175 said:**
> W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263. 
The wine error is because you dont have the key for the repositories:
```

wget http://wine.budgetdedicated.com/apt/387EE263.gpg
gpg --import 387EE263.gpg
sudo apt-key add 387EE263.gpg

```
> 
oh, and i don't know which one i'm running whether i'm running GNOME, or KDE.... how do i tell?

Well are you running Ubuntu or Kubuntu - it will tell you in huge letters when you log in. If its ubuntu its Gnome, if its Kubuntu its KDE (unless of course you put on a different desktop environment)
> **Jeroen Vernooij said:**
> For Wine, you can also just browse to [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) and download the .deb and run it, I think. That's a lot easier than fooling around with repositories and associated GPG keys.
It only takes a small while to find out how to get the key, and then you can just use synaptic for it, which is a much better process for a beginner as it moves you through the steps of using synaptic and gets you comfortable with the setup.
Il

---


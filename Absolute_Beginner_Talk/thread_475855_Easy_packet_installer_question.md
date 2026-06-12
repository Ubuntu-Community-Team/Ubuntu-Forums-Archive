---
title: "Easy packet installer question"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Haruko147 on 2007-06-16
Just used linux for the first time yesterday so bear with me ^^

Ok, so I have mozilla firefox english and I want the french version. I go to the web site and download the linux package for french and I have a folder on  my home directory called firefox with all the french version file goodies inside.

Normally in windows I'd just open up the .exe and install right over my old firefox. However when I do ```
 sudo apt-get install firefox 
``` it tells me its already the most recent version avaiable. I've tried going into add/remove and synaptic, but maybe I missed the option to install the particular package, as it only shows the firefox english I already have installed.

Thanks in advance for the response!

---

### Post by starcraft.man on 2007-06-16
Went through the hard way... the repos contain the french localized version of firefox.

First of all, aptitude is mostly for installing things via repos. I am gonna assume what you downloaded was an archived version of the source... not needed. You directed aptitude to install the default (english) version of Firefox which is already installed.

Open the terminal and paste this in:

```
sudo aptitude install mozilla-firefox-locale-fr-fr
```

That will give you the french version I believe. In future when your looking for something in the repos, I find the easiest way to search from the terminal is:

```
sudo aptitude search "x"
```

take off the "" and just substitute the name for x.

If you prefer the GUI, go System > Administration > Synaptic Package Manager and push search. It will get you a prettier readout.

[Oh and this is a good guide]("http://www.psychocats.net/ubuntu/installingsoftware") (and site) for understanding how to install in general, including source.

I hope that was clear enough :).

---

### Post by Haruko147 on 2007-06-16
ok thanks, I think that will work

for the web site too, I think I getting a handle on these repositories. Its a bit foriegn from windows

---


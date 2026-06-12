---
title: "Help with Wireless"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by eejayb on 2006-10-15
Hi
I have until recently only dabbled with 'live CD' Ubuntu for teaching purposes. Showing students an alternative to that Bill Gates stuff.:-k 
I have now set up my main PC with removeable rack hard drive setups and installed Ubuntu 6. I am new to configuring Ubuntu and need some help. If I am to run Ubuntu as my default op sys I need internet access. Currently having to use my Win XP rack so I can get to the internet. I do use Mozilla firefox so as to avoid that IE thing. Sometimes I even use Netscape but never have liked IE.
Anyway my problem is I need step by step guidance on getting my D-Link DWL 520+ card to function on Wlan0.:confused: 
I have supplied the network name and WEP but to no avail.:mad: 
I have a Win XP laptop and will have to keep it on this Op Sys until the main PC is sorted then I will go all out Ubuntu at home and try to get an Ubuntu Network set up at college.:rolleyes: 
Any help or advice greatfully received even if it is to tell me of a good book that will help my knowledge expand.

EEjayb

---

### Post by kingjere on 2006-10-15
your first stop should be here.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D)

to see if your card is supported.

your next step should be to 

```
sudo apt-get isntall ndiswrapper-utils ndisgtk
```

then cross your fingers and . . .
 I don't know where it shows up in the menu but ndisgtk is a graphical front end to ndiswrapper.

and finally, do your best to avoid ](*,)

---


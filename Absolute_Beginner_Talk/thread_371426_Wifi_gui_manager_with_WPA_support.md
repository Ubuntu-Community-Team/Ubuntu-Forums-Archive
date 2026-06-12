---
title: "Wifi gui manager with WPA support?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2007-02-26
I just installed edgy and I am trying to setup the wireless.  It appears as though my wireless manager doens't have WPA support.  How can i connect to a network with wpa?

Thanks 
-Hans

---

### Post by sardion on 2007-02-26
Install network-manager
It is in synaptic.
It has the best support for WPA of any of the GUIs (its not perfect but its pretty good).

---

### Post by CCBalla10 on 2007-02-26
> **sardion said:**
> Install network-manager
It is in synaptic.
It has the best support for WPA of any of the GUIs (its not perfect but its pretty good).

I agree totally..i also use network-manager and haven't had any issues yet!
Yay! for Ubuntu!

---

### Post by Bez625 on 2007-02-26
Hi I dont know if this helps but i recently had trouble on Dapper with wifi wpa and found this link very useful 

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

-Bez

---

### Post by hansoffate on 2007-02-27
i searched for network-manager when in Add/remove programs and nothing was found.  Any ideas?

Thanks
-Hans

---

### Post by Bez625 on 2007-02-27
Hey mate I hope im not being patronising but i think you're in the wrong add/remove programs part, you're looking for the synaptic package manager and you want to search that. If you go in to the Administration tab then to synaptic package manager and this should prompt for your password then allow you to search your package lists. Search there for it.

-Bez

---

### Post by hansoffate on 2007-02-27
Oh, I am using Kubuntu.  I forgot to mention that.  Is it any different.  When i try to install ubuntu-desktop through Add/Remove software, it always fails.  I really would like gnome to be installed. As well as that network manager.

Thanks
-Hans

---

### Post by H.E. Pennypacker on 2007-03-01
> **hansoffate said:**
> Oh, I am using Kubuntu.  I forgot to mention that.  Is it any different.  When i try to install ubuntu-desktop through Add/Remove software, it always fails.  I really would like gnome to be installed. As well as that network manager.

Thanks
-Hans

Ah, shoot.  I don't know if Kubuntu even has Synaptic, but I think it does.  I used to use PCLinuxOS, and I am pretty sure I used to use Synaptic under Kubuntu.

Just as a note, it's best to use what everyone else is using (in this case, Gnome).  That way, all the instructions make sense.  

As far as WPA support, check out [Wicd Manager]("http://compwiz18.blackhole.cx/wicd/wb/").  Lots of people report positive news, but it may have other bugs that could be a pain.  It is not as mature as Network Manager, but it is quickly surpassing Network Manager.

---

### Post by wieman01 on 2007-03-01
> **H.E. Pennypacker said:**
> Ah, shoot.  I don't know if Kubuntu even has Synaptic, but I think it does.  I used to use PCLinuxOS, and I am pretty sure I used to use Synaptic under Kubuntu.

Just as a note, it's best to use what everyone else is using (in this case, Gnome).  That way, all the instructions make sense.  

As far as WPA support, check out [Wicd Manager]("http://compwiz18.blackhole.cx/wicd/wb/").  Lots of people report positive news, but it may have other bugs that could be a pain.  It is not as mature as Network Manager, but it is quickly surpassing Network Manager.
Funny note recommending what "everyone else is using" (GNOME) and at the same time offering "Wicd" which is not part of the official repository. But I concur, lots of people do indeed report positive news concerning the tool, so it's worth a try.

I heard the final version of Feisty will integrate NetworkManager by default, so let's hope for the best. Guess all our concerns will be history by the time it comes out.

---

### Post by Jussi01 on 2007-03-01
> **hansoffate said:**
> Oh, I am using Kubuntu.  I forgot to mention that.  Is it any different.  When i try to install ubuntu-desktop through Add/Remove software, it always fails.  I really would like gnome to be installed. As well as that network manager.

Thanks
-Hans

Ok, first, do you have internet access? most of the add remove stuff you will need internet access for. You may have to turn off your wpa for a few minutes to get everything working. now to add gnome, once you have your internet working, you can go to terminal - not sure where it is in kubuntu but its somewhere in the menu's, then type this:

```
sudo aptitude install ubuntu-desktop
```

Enter your password

and it will install.

---

### Post by groggyboy on 2007-03-04
kubuntu by default uses a program called adept (instead of synaptic).  you can still install synaptic if you wish - it has no extra dependencies.

network manager still works under KDE - try searching/installing knetworkmanager.  from the terminal, it would be this:```
sudo aptitude install network-manager knetworkmanager
```

---


---
title: "Wireless Managment"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Sizzlintrumpet on 2007-03-05
Okay I would like to state that I am new to Ubuntu, and I have no problems connecting to any wireless network...except...

I am finding it a pain to configure my wireless card everytime I switch wireless networks to lets say my secure wireless network (with password) to my schools wireless network...with no password.

Each time I have to change the network name...by hand...and add passwords...by hand. It's getting a pain to keep changing things over and over again, when I move from the dorms to the school. 

My question: Is there a network manager that would make things easier...perhaps memorizes my passwords and network names, so I don't have to manually type them in? As an added bonus could this program search out unknown networks as well?

---

### Post by oilchangeguy on 2007-03-05
download and install automatix. [www.getautomatix.com](www.getautomatix.com). open the program check the box to enable debian unsupported software. under internet the list should show a wireless snifer program. this should meet your needs.

---

### Post by moffa on 2007-03-05
Use network manager by running 

```
 sudo aptitude install network-manager-gnome 
```

or graphically install network-manager-gnome with Synaptic

The only annoying thing is it asks you for the keyring password every time you login.

---

### Post by Ek0nomik on 2007-03-05
Rather than downloading automatix, which wastes extra space if he doesn't want all of the extra stuff, just download the program itself, disregarding automatix.

You can also download "Network Manager".  If you run a search in the Ubuntu Forums it should prompt you with some HOW TO's,

Cheers!

---

### Post by RomeReactor on 2007-03-05
Hi. I think both WiFi-Radar and Network-Manager-Gnome do what you want, though i haven't tried them that much. Look for them in Synaptic.

---

### Post by Ek0nomik on 2007-03-05
> **RomeReactor said:**
> Hi. I think both WiFi-Radar and Network-Manager-Gnome do what you want, though i haven't tried them that much. Look for them in Synaptic.

I personally haven't had any issues with Network Manager.

---

### Post by Sizzlintrumpet on 2007-03-05
Thanks for all the input guys, network manager sounds like a good idea to me. So I'm gonna give it a shot, I'll post if I have any problems.

---

### Post by Ek0nomik on 2007-03-06
Just fyi, if while playing around with your panels, you accidentally remove your Network Manager, if you right click and add the Notification Area, it will reappear.

Cheers!

---


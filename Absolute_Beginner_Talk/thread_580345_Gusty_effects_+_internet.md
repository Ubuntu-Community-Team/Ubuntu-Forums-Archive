---
title: "Gusty effects + internet"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by natman on 2007-10-18
Hi i just my upgrade to gusty everthing seems to be fine except my internet speed which seems a good deal slower since the upgarde? anyone else have this problem?
also a question about the desktop effects, once i have selected the hight end option , can i cutomize any further, ie make windos in the backround go even more transparent?

---

### Post by RomeReactor on 2007-10-18
Hi. Look for **compizconfig-settings-manager** in Synaptic (System->Administration->Synaptic); or to install it from the terminal:
```
sudo apt-get install compizconfig-settings-manager
```

Once that's installed, you'll find it in "System->Preferences->Advanced Desktop Effects Settings", or you can access it through "System->Preferences->Appearance->Visual Effects", select the "Custom" option and press "Configure".

---

### Post by natman on 2007-10-18
managed to solve the internet problem
by using an old solution

1: sudo gedit /etc/modprobe.d/aliases
2: find the line - alias net-pf-10 ipv6
3: Edit this to alias net-pf-10 off
4:save and reboot
5: IF that does nothing try line 3) with .... off ipv6
6:It should now surf alot faster

---

### Post by swoll1980 on 2007-10-18
> **natman said:**
> Hi i just my upgrade to gusty everthing seems to be fine except my internet speed which seems a good deal slower since the upgarde? anyone else have this problem?
also a question about the desktop effects, once i have selected the hight end option , can i cutomize any further, ie make windos in the backround go even more transparent?

it's the dns settings. this happend to me. you have to go to network settings put your dns settings in manually and then enter "sudo chattr +i /etc/resolv.conf" This will lock the file and keep it from being reset. to unlock it in the future just use the same command but use a - instead of a + with mine my modems address was being added to my dns servers so I just deleted it from the list then enterd the command above . hope this works for you

---


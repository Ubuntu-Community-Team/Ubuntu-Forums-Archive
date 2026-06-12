---
title: "Firewall question"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by NiksaVel on 2006-10-30
Okay, just a short n00b question :)


firestarter, guarddog and similar firewall solutions for linux function by simply injecting specified parameters into the iptables, right?


The question is:  do they make permanent changes to the iptables config or do I have to run firestarter every time I start linux?


thanks!

---

### Post by JayTee on 2006-10-30
The changes they make are permanent until you undo them in Firestarter, etc. Firestarter is just a GUI frontend to iptables. I've never used the others so I'm not certain of them.

---

### Post by NiksaVel on 2006-10-30
thnx!

---

### Post by cornelis1 on 2006-10-30
I believe that firestarter is the gui for the firestarter deamon. As far as I know, it is the deamon which "injects" the changes into iptables. So, when the deamon doesn't run in the background (this can sometimes happen if you use network-manager with a wireless networkcard) the changes don't load into iptables (which therefore are not permanently changed by firestater). Please correct me if I,m wrong.

---


---
title: "Different internet connection problem"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by MickS on 2007-07-21
I have searched but I can't find what I am looking for, I am running 7.4 with KDE and Ethernet connection, normally everything works fine but every now and then my Livebox router loses the internet for a minute or so and Ubuntu gets disconnected from the net. Question is how do I get it to reconnect without rebooting, I cannot find anything to click on and it doesn't do it automatically, I am sure I am missing something obvious but for the life of me I can't think what.

TIA

Mick

---

### Post by DBStevens on 2007-07-21
Could you zip up or tar your /var/log/daemon.log files there are several as they get rotated and place them somewhere and provide a link.

The system should attempt lease check and acquire actions provided it sees the link change state.

If for some reason the link state doesn't change then the system won't do anything and it will act as it should for what it understand as its current state.

Something along this line should appear if the link reactivates:

 NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link.

---

### Post by Majorix on 2007-07-21
What about
```
sudo /etc/init.d/networking restart
```
?

---

### Post by DBStevens on 2007-07-21
That'd do it.

However even that shouldn't be required.

---

### Post by MickS on 2007-07-21
Thanks guys, I have copied the sudo command and pasted it on a sticky for next time it happens, got to be honest I don't know how to do the other thing.
It's not a mayor issue for me because it doesn't happen very often but it would be nice to get it sorted.

Mick

---


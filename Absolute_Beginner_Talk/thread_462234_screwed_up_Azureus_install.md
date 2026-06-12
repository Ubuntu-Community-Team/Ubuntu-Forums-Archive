---
title: "screwed up Azureus install"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by abburdlen on 2007-06-02
First of all thanks to everyone here.  I finally got fed up with microsoft and made the switch to ubuntu.  I flirted with linux years ago (mandrake 5, i think) but it didn't work out.  Ubuntu has worked pretty much right out of the 'box' and in the few places where it hasn't I was able to find instruction here in the forum.

Now however I think I've screwed something up.
I installed Azureus with automatix (yeah, I know...) and all seemed fine but I'd open torrents and they wouldn't start to download.  I thought perhaps it was something messed up with how Automatix set it up so I removed it and installed from the terminal 
```
sudo apt-get install azureus
```
Now Azureus shows up in applications but fails to start.

My question is 1) how does one uninstall after using apt-get and 2) what is the correct way to get Azureus working?

---

### Post by Seisen on 2007-06-02
To uninstall Azureus, do this in the terminal

```
sudo apt-get remove azureus
```

the second problem could be firewall related, Do you have a firewall or router?

---

### Post by abburdlen on 2007-06-02
```
sudo apt-get *remove* azureus
```
darn you linux and your cryptic commands!;)

I've got a router but azureus would report green on the NAT.  I'll try installing again and get more info.

---

### Post by CREEPING DEATH on 2007-06-02
Azureus from the repos has not worked in Ubuntu since 6.06

CD

---

### Post by milambyr on 2007-06-02
Taken from another thread (and this happens to me every now and than with Azureus) try in the terminal:

rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

Edit: I'm using 7.04 and it works fine Creeping Death.  Sometimes Azureus won't start and this is usually because of a system crash or reboot while Azureus is still running.

---


---
title: "Firestarter question"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2006-12-15
Hello everyone;

Just a quick question.....

I installed Firestarter. I work from work and the road a lot, so I am in need of it. Now I added it to my starting session with this starter command "gksu Firestarter" (I copied it from my desktop icon command). Firestarter does start now every time I boot up, however it is asking me for my admin password stating it is going to make some changes in root.

Now finally to the question....

Is that right? and how can I get it to boot with having it ask me for the admin password?

Thanks again people for all your help!

I LOVE UBUNTU (deleted my Windows XP partition, using Ubuntu only!!:mrgreen: )

---

### Post by loyaleagle on 2006-12-15
I meant .....

Without it asking me for the admin password...

Sorry!

---

### Post by frodon on 2006-12-15
First you have to know that you don't need the GUI opened to have firestarter running. Your firewall is automatically started by default on boot.
You can check this with this command :
```
sudo /etc/init.d/firestarter status
```You need the firestarter interface only when you want to modify some rules or swich off the firewall, it is running by default.

So don't worry, when you boot your firewall is already activated ;)

---

### Post by tocleora on 2006-12-15
I've seen this question answered a lot on this forum though.  You should be able to search for "firestarter" and find the answer if you still want the gui to start when you start x windows.

---

### Post by loyaleagle on 2006-12-15
Thanks.... Once again you are the master of Ubuntu. The help here is fantastic here for a Linux newbie like myself. I assumed it has to be running in the tray, a la Windows XP, for it to work. It will take me a while to get out of that mode of thinking.

I LOVE UBUNTU!!!!!!!!

---

### Post by FLPCGuy on 2006-12-15
> **frodon said:**
> First you have to know that you don't need the GUI opened to have firestarter running. Your firewall is automatically started by default on boot.
You can check this with this command :
```
sudo /etc/init.d/firestarter status
```You need the firestarter interface only when you want to modify some rules or swich off the firewall, it is running by default.

So don't worry, when you boot your firewall is already activated ;)

I've installed Firestarter via Synaptic but it doesn't seem to be running; I get no response from the cmd you indicated.  Also, there is no indication of the application in my Apps menu.  It is listed as installed.  What am I missing?  

I just remembered, there is a more basic problem.  

Ubuntu networking still won't see or use my external serial (full) modem.  I had to download and install KPPP via terminal ppp which works fine, but the system never detects this connection and no configuration of networking will activate a dial-up connection to either /dev/modem or /dev/ttyS0.  I think solving this issue will solve the firestarter problem (I finally found it under System Admin).  It only sees my inactive nic eth0 just like Networking.

---


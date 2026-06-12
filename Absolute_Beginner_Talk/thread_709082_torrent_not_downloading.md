---
title: "torrent not downloading"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Jacques Kleynhans on 2008-02-27
I have recently installed azureus but its not downloading i did correct port forwarding in my router i have no nat problem always get green smiley have added the ports to my firestarter. Its weird any one have similar problem??

---

### Post by uberlube on 2008-02-27
Ive had similar problems with it. Went over to Deluge and everythings dandy now! :) Plus its lightweight.

---

### Post by Jacques Kleynhans on 2008-02-27
thx ill give it a try

---

### Post by Jacques Kleynhans on 2008-02-27
well i installed deluge but still not downloading when i test port it says

TCP port 45000 closed on 196.25.255.250

??

---

### Post by uberlube on 2008-02-27
Did you assign port 45000? And is that the one you forwarded? Also give port 8661 - 6889 a try.

---

### Post by uberlube on 2008-02-27
Also compare the way you open your ports with this guide to see if youve missed something.

[http://forums.afterdawn.com/thread_view.cfm/223583](http://forums.afterdawn.com/thread_view.cfm/223583)

---

### Post by Jacques Kleynhans on 2008-02-27
in my router i forwarded ports 45000-65000

---

### Post by Jacques Kleynhans on 2008-02-27
TCP port 6881 closed on 198.54.202.195

for some reason

---

### Post by uberlube on 2008-02-27
> TCP port 45000 closed on 196.25.255.250

This means that you missed a step somewhere along the line. Try tracing your steps backwards to make sure. i believe that the oprt has to be opened and then forwarded. 2 different processes. Ive tried to figure it all out before but couldn't. Then I started getting faster downloads so I forgot about it.

---

### Post by misfitpierce on 2008-02-27
Some ISP's are throttling torrent activity... Always make sure to change default port of torrent traffic and use encryption.

---

### Post by uberlube on 2008-02-27
When you say change the default port do you mean change lets say port 6881 to whatever other one or are you talking about something else?

---

### Post by TeoBigusGeekus on 2008-02-27
> **uberlube said:**
> Did you assign port 45000? And is that the one you forwarded? Also give port 8661 - 6889 a try.
Ports 6881-6889 are banned by some ISPs because they are the default bittorrent ports.
Try to install &#956;torrent via wine, disable the options regarding the tray icon, give it your open port(45000) and run it's port forwarding test.

---

### Post by misfitpierce on 2008-02-27
No there is no reason to use uTorrent and run it through Wine... Deluge or Transmission will work fine in linux unless ofcourse you choose to use  a windows app but it is not necessary. Encryption and changing of port works fine.

---

### Post by TeoBigusGeekus on 2008-02-27
The only reason I suggested &#956;torrent is because I had similar problems with Deluge (Ports forwarded through router and firestarter but Deluge not being able to see them).
Of course I prefer Linux applications to Window$ ones, but sometimes....:confused:

---

### Post by Jacques Kleynhans on 2008-02-27
the thing is i ma trying deluge but is still says my ports are closed i have disabled firestarter in an attept to resolve but still ni change

---

### Post by TeoBigusGeekus on 2008-02-27
Try a reboot or &#956;torrent.

---

### Post by Jacques Kleynhans on 2008-02-27
Why is this not working i have tried bittorent , azureus , deluge some where im doing something wrong. Is there an how to i can look at

---

### Post by Jacques Kleynhans on 2008-02-27
i have tried rebooting but i i said previously i have tried those other bittorents to but nothing seems to work...

---


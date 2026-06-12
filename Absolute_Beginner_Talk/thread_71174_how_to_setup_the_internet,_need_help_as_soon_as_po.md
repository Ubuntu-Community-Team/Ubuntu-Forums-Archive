---
title: "how to setup the internet, need help as soon as possible."
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by Aven on 2005-10-02
Ok, I run servers on my computer and I used to run an ircd and apache server on WINDOWS. I decided to get a better OS to run on servers so I'm going to try out Ubuntu Linux.

However, I have no idea on how to setup the internet. I use cable and it's all plugged in but somehow won't work.

I know it's in the Networking or Network tools somewhere, I played around with it and still have no idea how to get it working.

Can someone please point me to a link that describes step-by-step? or could you at least tell me step-by-step?

I need to get my servers runnning again! please help as soon as possible.


Thank you.

---

### Post by Ruddigger on 2005-10-02
If you have cable modem, then dhc should detect everything with no problem.
The only thing is that some cable modem providers (at least Adelphia does) have things set up in some way (I don't know the technical info) but I had to call and say I have linux, I can't connect. They fix something on their end, and then it works...
maybe this is your case?

---

### Post by Aven on 2005-10-02
That was helpful Ruddiger.

I still can't get it to work though.

Ok, questions :P

1) I went on "Network Settings" and I looked in connections. I saw the Interface "eth0" and it said it's active. What exactly is eth0?

I also clicked on "Properties" and I have it on "DHCP"

So, what exactly is ech0? anyone know?


thanks!

---

### Post by ProPilot on 2005-10-02
eth0 is the 'address' (name) of the interface card in your computer. You would see ath0 or wlan0 is you had wireless. I use Breezy in System-Administration-Networking click on the ethernet connection line so it is highlighted, ensure it is active, then select properties and make sure either DHCP is selected or static IP and that info depending on the connection and setup you have.

---


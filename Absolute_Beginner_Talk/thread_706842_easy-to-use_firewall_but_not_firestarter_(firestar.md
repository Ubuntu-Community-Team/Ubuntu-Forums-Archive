---
title: "easy-to-use firewall but not firestarter (firestarter runs unstable)"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by thomas7.10 on 2008-02-24
Hi again!

(i hope i don't write to much in this forum with my bad English)

Now after 7-10 hours of working on my firewall, dns, dhcp computer i finally got all to work. Unfortunately firestarter is now turning out to be totally unstable on my system. I start it and then after a couple of minutes it just disappears from the screen without leaving a trace.

I would be perfectly fine if it would just start again after it disappeared but it doesn't.

So does anyone know a firewall that as easy to use as firestarter and work more reliable?

Thanks in advance!

Thomas

---

### Post by skyjacker on 2008-02-24
> **thomas7.10 said:**
> Hi again!

(i hope i don't write to much in this forum with my bad English)

Now after 7-10 hours of working on my firewall, dns, dhcp computer i finally got all to work. Unfortunately firestarter is now turning out to be totally unstable on my system. I start it and then after a couple of minutes it just disappears from the screen without leaving a trace.

I would be perfectly fine if it would just start again after it disappeared but it doesn't.

So does anyone know a firewall that as easy to use as firestarter and work more reliable?

Thanks in advance!

Thomasfirestarter is just a graphic interface for the built-in firewall iptables. You should not need any other firewall.

---

### Post by seventhc on 2008-02-24
It's also still running, if you want it to always show then I think you have to change that in the preferences.
But even though you don't see it, it is in fact still running.

---

### Post by seventhc on 2008-02-24
to test if it's running, open a terminal and paste this in.
```
sudo /etc/init.d/firestarter status
```

---

### Post by seventhc on 2008-02-24
sorry, not sure why but it posted more than once. :confused:
deleted.

---

### Post by thomas7.10 on 2008-02-24
Oh ok.

Is there some possibility to check whether this iptable thing is running or not?

Thomas

---

### Post by seventhc on 2008-02-24
firestarter is using iptables, it just gives you a gui to work with.
So if your using firestarter and it's running, then so is iptables.

---

### Post by thomas7.10 on 2008-02-24
thanks for your help!

Cool signature by the way. You can't imagine how i felt when i first saw google on the laptop.

---

### Post by seventhc on 2008-02-24
Thanks :)
What do you mean about google...you mean like to many pages??:D

---

### Post by thomas7.10 on 2008-02-24
oh sorry you don't know about my day.

It took my about 10 hours to make it possible that my ubuntu PC is sharing it's internet connection with 3 other PCs over a netgear router.

When i finally got the right settings on one of the PCs and it was possible to go on the google website i thought: WOW it's working now but no one will ever got to know how hard it was to get here.

---

### Post by seventhc on 2008-02-24
ahh, yeah..I know that feeling. :)

---

### Post by northern lights on 2008-02-24
> **thomas7.10 said:**
> It took my about 10 hours to make it possible that my ubuntu PC is sharing it's internet connection with 3 other PCs over a netgear router

Grand you got it working. Why a firewall in the first place? My firewall is in my router...

---

### Post by seventhc on 2008-02-24
> **northern lights said:**
> Grand you got it working. Why a firewall in the first place? My firewall is in my router...
Your Ubuntu also has a firewall, it's called iptables and it starts up when you boot up by default. Firestarter just makes it easier for configuration. ;)

---

### Post by northern lights on 2008-02-24
I'm aware of iptables - if you're behind a router though, most of the time that's got an in-built hardware firewall. Does the job better than anything else...

---

### Post by thomas7.10 on 2008-02-24
I had the router in first place but it didn't work. I live in Sweden and we have a ethernet slot directly in the wall. You don't have to use a username or password it should just work but it doesn't sometimes the internet is getting really slow or it just stops to work and then you have take away the power supply from the router for 20 sec. and then it works again for a uncertain time. It can get quiet annoying. The local internet provider told us that something is wrong with our router.

It is quiet strange how the hold thing is organized if i go in to network on the common gnome interface i see Samba servers from people that are not directly connected to my workgroup. Then i got UDP packages on very high ports from my own IP external IP adress and samba packages from people with nearly the same IP adress. (I mean only numbers after the last point are different from mine - don't now probably there is a technical word for that...)

Maybe the router was so busy dealing with all this packages and therefor the internet got that slow.

Or do you know something about that?

---

### Post by thomas7.10 on 2008-02-24
So here it's now 4 am local time - time to go to bed.

---

### Post by seventhc on 2008-02-24
ok, ttyl later, if you need help just ask. Not sure about your slow traffic atm, if I think of anything I'll post it here.

---


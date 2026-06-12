---
title: "Question about Firestarter"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by disc on 2006-11-01
I've successfully installed Firestarter, and can run it through the terminal, but is there a way to run Firestarter without the terminal? It does not show up under Applications, nor does it show in Alt+F2. Any suggestions?

---

### Post by raqball on 2006-11-01
How did you install it? 

You do realize that for the most part it will just sit and eat memory. It really has nothing to do since all ports are already closed..

---

### Post by disc on 2006-11-01
I installed it through Synaptic Package Manager. I guess I don't really need it, but it offers a nice peace of mind.

---

### Post by OffHand on 2006-11-01
> **raqball said:**
> How did you install it? 

You do realize that for the most part it will just sit and eat memory. It really has nothing to do since all ports are already closed..

What memory? It's a frontend to configure ip tables which are always 'on'.
To the OP: maybe you need to restart you gnome-panel:
```
sudo killall gnome-panel
```
You should find an icon under System > Administration or under Applications > Internet.

---

### Post by raqball on 2006-11-01
It's probably listed under System >> Administration :)

EDIT: Offhand beat me to the punch! Glad it's now working for you :)

---

### Post by disc on 2006-11-01
> **OffHand said:**
> To the OP: maybe you need to restart you gnome-panel:
```
sudo killall gnome-panel
```
You should find an icon under System > Administration or under Applications > Internet.

Thank you very much, it's now appearing under System > Administration.

---

### Post by raqball on 2006-11-01
> **OffHand said:**
> What memory? It's a frontend to configure ip tables which are always 'on'.


Are you implyinmg that when it sits in the system tray (notification area) that it does not use any memory to run? If so that's a very interesting suggestion :)

---

### Post by OffHand on 2006-11-01
> **raqball said:**
> Are you implyinmg that when it sits in the system tray (notification area) that it does not use any memory to run? If so that's a very interesting suggestion :)

Firestarter is always loaded (daemon). It doesn't have to be in the sys tray to work. 
And even if it's loaded it probably uses only a few MB. That's nothing on modern machines.

---

### Post by raqball on 2006-11-01
> **OffHand said:**
> Firestarter is always loaded (daemon). It doesn't have to be in the sys tray to work. 
And even if it's loaded it probably uses only a few MB. That's nothing on modern machines.

You are correct Sir. But as I stated it eats memory for no real reaon as in my opinion it's not needed. If you have 1024mb of memory it's no big deal. If you are using 128 or 256 then every drop of memory counts (even 2mb)

:)

---

### Post by Tweedicus on 2006-11-01
My two pence worth:

It disabled my wifi connection and ethernet connection. A complete balls up. I had to uninstall Firestarter, then restart my system to get everything up again. 

Not sure I would recommend it to anyone.

Thanks but no thanks.

---

### Post by disc on 2006-11-01
> **Tweedicus said:**
> My two pence worth:

It disabled my wifi connection and ethernet connection. A complete balls up. I had to uninstall Firestarter, then restart my system to get everything up again. 

Not sure I would recommend it to anyone.

Thanks but no thanks.

It disabled my ethernet connection as well, but a few teaks in the Preferences fixed it.

---

### Post by bpalyshka on 2006-11-02
thanks alot this was very helpful.

---

### Post by doobit on 2006-11-02
Firestarter is a great little firewall program. I keep hearing that all it is is a frontend to IPtables, but that's not exactly true. It has a complex set of instructions that allow you to set up different profiles and filtering, gives you real time port monitoring in and out, allows you to deny broadcasting to and from certain ports, say if you get a spam bot or script kiddie messing around with you (and it does happen - FireStarter allowed me to see it.), allows you control of port forwarding and tunneling, and even can perform internet sharing from a gateway computer if you don't have a router.
I also wanted to add, that having it running in the tray allows you to instantly see events, such as rejected packets, when they occur. When you visit certain websites, they will send outbound information back to the site's data collection agency, or server, or whatever they use. Firestarter gives you the option of closing that port or denying broadcast to that address of hostname.

Firestarter has to be run as root, BTW , which may have been the source of your original problem.

---


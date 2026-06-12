---
title: "Do I need AVP &amp; Firewall protection?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by lakestony on 2007-07-10
Hi there

New to Ubuntu which I finally managed to load on my very old HP Pavilion laptop.

I've been thru Microsoft from Dos to XP and did Pascal at the Open Uni so I think I can deal with command lines etc.

Anyway, my question 

Do I need and AVP or Firewall in Ubuntu on the laptop?

I use CA AVP and ZoneAlarm on my PC (a local OEM) and AVG and Zonealarm on my other Laptop (Advent)

both of which are running Win XP Home SP2 as was the Pavilion before I wiped itfor Ubuntu.

TIA

Tony

---

### Post by Nekiruhs on 2007-07-10
*buntu comes with a firewall called IPTables. Its CLI only but you can get a GUI for it via Firestarter (Gnome Themed) or Guarddog (KDE Themed).  The GUIs give you a way to configure the firewall without having to use the terminal. You dont really need Antivirus/Antispyware/Antimalware unless your worried about passing on email viruses to windows users.

---

### Post by lakestony on 2007-07-10
thanks for the prompt response

as a newbie

how do I do this please? and

which is the best option?

tia

tony

---

### Post by Inxsible on 2007-07-10
> **lakestony said:**
> thanks for the prompt response
 
as a newbie
 
how do I do this please? and
 
which is the best option?
 
tia
 
tony
 
Do you mean how do you get firestarter ?
 
```
sudo aptitude install firestarter
```

---

### Post by sugarland2k on 2007-07-10
Unless your running a server, web server, etc.  You probably do NOT need AVP and/or Firestarter in Ubuntu/Kubuntu as ports are quite secure.  

I do run a good virus scanner and firewall in Windows XP since this O/S needs this on the net but Linux is quite secure.  

Relax it's Ubuntu! :)

---

### Post by lakestony on 2007-07-10
Thanks 

I want IPTables as a GUI

Do I first install Firestarter with the command you suggested and then look for IP Tables or what

Sorry

TIA

Tony

---

### Post by p_quarles on 2007-07-10
> **lakestony said:**
> Thanks 

I want IPTables as a GUI

Do I first install Firestarter with the command you suggested and then look for IP Tables or what

Sorry

TIA

Tony
No, it's part of the installation. By default, it blocks incoming services on all ports. You can change this by adding rules to the config file.

EDIT: Misread "GUI" as "CLI." Der. Anyway, once you install Firestarter, you'll find it (under that name) in the System >> Admin menu.

---


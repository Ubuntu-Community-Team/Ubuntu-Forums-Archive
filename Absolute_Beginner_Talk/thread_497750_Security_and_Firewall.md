---
title: "Security and Firewall"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-07-10
Hi, I would like to make sure I am as protected as possible from hackers and viruses. I know that viruses are not really a problem in Ubuntu, but I would like to make sure I have a good firewall runnning, the default Ubuntu one should be fine if it is known to be good. How do I enable the firewall or is it just defaulted on and Ubuntu is just good like that. ;)

---

### Post by mlentink on 2007-07-10
Your firewall is called iptables, and it is enabled by default. 

Welcome to the free world...

---

### Post by Malibu Illusion on 2007-07-10
You may wish to go ahead and install a graphical front-end for iptables:

```
sudo aptitude install firestarter
```

---

### Post by Inxsible on 2007-07-10
If you want a GUI to access the iptables, you can install firestarter
 
EDIT : Too late :rolleyes:

---

### Post by mr.v. on 2007-07-10
go to System | help and support | and type in "Firewall"

---

### Post by Astrikor on 2007-07-10
You probably need firestarter
open "System/Administration/Synaptic Package Manager"
hit "Reload"
locate "firestarter" in the Package list & check its  box
choose "mark for installation"
choose "Apply"

---

### Post by John.Michael.Kane on 2007-07-10
Heres how to edit your iptables via the command line [Set a custom firewall (iptables) and Tips]("http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables").

---

### Post by kavon89 on 2007-07-10
How do I open the GUI version of Firestarter thing? It doesn't show in Internet section of Applications or in the System menu.

---

### Post by steve.horsley on 2007-07-10
> **mlentink said:**
> Your firewall is called iptables, and it is enabled by default. 

Welcome to the free world...

This is misleading. 
The default configuration for iptables (which, as you say, is enabled by default) is to permit everything.

HOwever, unless you choose to install some services, there are no open ports for a configured firewall to protect.

---

### Post by kavon89 on 2007-07-10
> **steve.horsley said:**
> This is misleading. 
The default configuration for iptables (which, as you say, is enabled by default) is to permit everything.

HOwever, unless you choose to install some services, there are no open ports for a configured firewall to protect.

So am I protected from an attack? :confused:

---

### Post by Inxsible on 2007-07-10
> **kavon89 said:**
> How do I open the GUI version of Firestarter thing? It doesn't show in Internet section of Applications or in the System menu.

Its in System -- > Administration --> Firestarter

---

### Post by Malibu Illusion on 2007-07-10
> **kavon89 said:**
> So am I protected from an attack? :confused:

Default installations of Ubuntu have nothing to protect.  There are no daemons listening on your ports to begin with thus making all of your ports closed.

---

### Post by mdsmedia on 2007-07-10
> **kavon89 said:**
> So am I protected from an attack? :confused:You are protected from an attack because no ports are open, by default.

Although the firewall (IPtables) is set to "allow everything", because nothing is open by default this should not be a problem.

The firewall can be configured to close ports if necessary, IF you have services open to allow certain access.

---

### Post by abn91c on 2007-07-10
check you PC security here [http://probemyports.com](http://probemyports.com)

---

### Post by Skidpad on 2007-07-11
> **abn91c said:**
> check you PC security here [http://probemyports.com](http://probemyports.com)
I am in no way a security expert, but I know some of the basics of ports, security, etc.  Provided the testing methods are true and accurate, it is a nice feeling to run a Linux machine through the tests on the link you posted.  I will do my XP machine tomorrow for a comparison.  :D

---

### Post by Astrikor on 2007-07-12
> **Astrikor said:**
> You probably need firestarter
open "System/Administration/Synaptic Package Manager"
hit "Reload"
locate "firestarter" in the Package list & check its  box
choose "mark for installation"
choose "Apply"


After it is installed as above, run Applications/System Tools/Firestarter to configure the firewall.  The firewall will now start in the background when your computer starts.

It worked for me!
Astrikor

---

### Post by 3rdalbum on 2007-07-12
If you are on ADSL, your modem/router may already have a firewall configured not to allow any incoming connections.

Unless you're going to start opening ports (installing servers, enabling SSH, changing CUPS settings etc), you don't need a firewall.

---


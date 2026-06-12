---
title: "Ubuntu anti virus"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Le 3eme Oeil on 2008-03-02
I was reading some other threads about anti virus and linux, but still didn't really find what i needed.  

Does anyone know of a guide or step by step that shows me how get get everything i need like anti virus, firewall, and anti spyware? 

that would be a big help:)

---

### Post by spiderbatdad on 2008-03-02
[http://linuxappfinder.com/node/643](http://linuxappfinder.com/node/643)

Also rkhunter in synaptic

---

### Post by SOULRiDER on 2008-03-02
No point in setting up anti virus or anti spyware, youre using a real OS.

For firewall you can install firestarter by typing
```
sudo aptitude install firestarter
``` in a terminal.

You might be interested in reading:
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) and maybe [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by Le 3eme Oeil on 2008-03-02
Ok thanks a lot, but ill have to check those out tomorrow i gotta get to bed for school. 

So far linux sounds great!

---

### Post by solitaire on 2008-03-02
Quick question regarding this...

On a dual booting machine does Linux antivirus spot a virus on the windows partitions if the NTFS reader is installed?

---

### Post by sumguy231 on 2008-03-02
> On a dual booting machine does Linux antivirus spot a virus on the windows partitions if the NTFS reader is installed?
I haven't used any of them, but I assume if the Windows partition is mounted and you tell it to scan it it will gladly do that.

---

### Post by SOULRiDER on 2008-03-02
And if it looks for windows viruses.

---

### Post by solitaire on 2008-03-02
I hope it will spot the Windows virri!!

if it does i'm gonna make up a Live CD with Antivirus on it and keep it around for when my mates comps die a virus riddled death... :D

---

### Post by JoshuaRL on 2008-03-02
Linux antivirus ONLY searches for windows viruses.  Because with Linux, there have been much less than 100 knows viruses/worms for the OS.  And all of those have never been in the wild, been patched out of existence, or both.

---

### Post by SOULRiDER on 2008-03-02
> **JoshuaRL said:**
> Linux antivirus ONLY searches for windows viruses.  Because with Linux, there have been much less than 100 knows viruses/worms for the OS.  And all of those have never been in the wild, been patched out of existence, or both.

Thats quite funny... and sad at the same time..

---

### Post by Oldsoldier2003 on 2008-03-02
> **SOULRiDER said:**
> No point in setting up anti virus or anti spyware, youre using a real OS.

For firewall you can install firestarter by typing
```
sudo aptitude install firestarter
``` in a terminal.

You might be interested in reading:
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) and maybe [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

Honestly if you dont install any server software on your Ubuntu workstation it's already locked down. Ubuntu is more secure "straight out of the box"  in that aspect then windows with a firewall. but when you start installing services that turn you into a server then you hsould definitely consider firestarter firehol or bastille.

---

### Post by JoshuaRL on 2008-03-02
> **Oldsoldier2003 said:**
> Honestly if you dont install any server software on your Ubuntu workstation it's already locked down. Ubuntu is more secure "straight out of the box"  in that aspect then windows with a firewall. but when you start installing services that turn you into a server then you hsould definitely consider firestarter firehol or bastille.

Right.  Ubuntu comes with a really great firewall, iptables.  Firestarter **ISN'T** a firewall, its a graphical front-end for iptables.  The default install of Ubuntu automatically shuts all the ports.

---

### Post by Oldsoldier2003 on 2008-03-02
> **JoshuaRL said:**
> Right.  Ubuntu comes with a really great firewall, iptables.  Firestarter **ISN'T** a firewall, its a graphical front-end for iptables.  The default install of Ubuntu automatically shuts all the ports.

The three apps i mentioned are all just front ends for iptables.Bastille is a hardening script that also sets up your iptables for you. Even though you start bastille-firewall, all it really does is make sure your iptables are set up when your computer boots.

---

### Post by vishzilla on 2008-03-02
No need for an anti-virus or anti-spyware s/w. Firestarter is required if you need to tweak the iptables, but its not mandatory.

---

### Post by oedha on 2008-03-02
> **solitaire said:**
> Quick question regarding this...
On a dual booting machine does Linux antivirus spot a virus on the windows partitions if the NTFS reader is installed?

you can scan the ntfs partitions and then remove the virus from that partitions.....as long as you have the latest virus definition data.......
i used AVG once....now...no need........

---

### Post by danielcc on 2008-03-02
check out f-prod there is a front end that makes it look pretty too... remember though that it would be kinda useless to run it on linux because its is just that uber great... i use virus scanners in linux only to fix windows systems...

---

### Post by wednesday allfather on 2008-03-02
I think that's cool.  When i first installed Ubuntu, migrating from windows, I went looking for antivirus software.  It's difficult to wrap your mind around not needing one.  

If you are a bit paranoid you can install chkrootkit.  It works quite well with rkhunter (posted earlier).

It checks for signs of intruder gaining root access to your computer.  Plus it is easy to use.

---

### Post by Le 3eme Oeil on 2008-03-03
Ok, so im really new and all this is still a little confusing. 

So all i need to do if i want firestarter is type that code, nothing needed to do prior?

---

### Post by julian67 on 2008-03-03
> **Le 3eme Oeil said:**
> Ok, so im really new and all this is still a little confusing. 

So all i need to do if i want firestarter is type that code, nothing needed to do prior?

I'd also read up about using firestarter, though it's not complex there are some things to know. There's some very good information (even essential if this is new to you) here: [http://ubuntuforums.org/showthread.php?t=542756]("http://ubuntuforums.org/showthread.php?t=542756")

and the firestarter home page is [http://www.fs-security.com/]("http://www.fs-security.com/")

---


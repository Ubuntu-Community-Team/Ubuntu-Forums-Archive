---
title: "One Last ? B4 the plunge........"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by ol_smokey on 2007-05-13
Just had a play around in a Live session and managed to get e-mail & internet working and can see the documents and files on my old Windoze drive OK. so it's looking quite likely I'm heading into the world of UBUNTU quite soon. I have one last question; I felt rather exposed browsing the net without a firewall, am I really safe? Not only from the viruses but spyware, tracking cookies etc..

Cheers
'Paranoid' ol_smokey

---

### Post by oilchangeguy on 2007-05-13
ubuntu has a built in firewall, it's called iptables. when you get it installed you can configure fire fox to delete the cookies, etc. when you close the browser.

---

### Post by finer recliner on 2007-05-13
by default. all ports are closed on ubuntu unless you launch an application that opens one of those ports.

if you plan to host a server (i.e. ssh, ftp...etc) i would download a wrapper for iptables from the repos.

in a nutshell...yeah you're safe with standard browsing

---

### Post by ol_smokey on 2007-05-13
> **finer recliner said:**
> by default. all ports are closed on ubuntu unless you launch an application that opens one of those ports.

if you plan to host a server (i.e. ssh, ftp...etc) i would download a wrapper for iptables from the repos.

in a nutshell...yeah you're safe with standard browsing

It's standard browsing I'm doing (vis cable broadband if it makes a difference).
So nothing can get itself onto my PC unless I download it?
If that's the case I'm in.
Just got to figure out how to do a dual-boot on 2 seperate drives. (Goes off to search in the archive)

Thanks guys

'Paranoid no-more' ol_smokey

---

### Post by heiko.nolen on 2007-05-13
I recommend the noscript add-on for firefox. - It'll decrease the amount of stuff you download even more.

Am not sure about the comparison with Firefox, but also the Opera web browser is said to be of the safest. Either way you're better off than with the Windows / IE combination...

This can all be installed through the System>Administration>Synaptic Package Manager so you don't even have to get into coding and stuff. The no-script add-on is downloaded through Firefox.

- Welcome to the club! :)

---

### Post by floke on 2007-05-13
You can install Firestarter from the repositories if you want a GUI for the Iptables firewall, although personally I find it to be a PITA so don't bother. It takes a while to get used to the fact that you don't need anti-virus etc. But relax, you're perfectly safe now :)

---

### Post by starcraft.man on 2007-05-13
> **heiko.nolen said:**
> 
Am not sure about the comparison with Firefox, but also the Opera web browser is said to be of the safest. Either way you're better off than with the Windows / IE combination...
- Welcome to the club! :)

Really? Well, I've never seen anything saying that firefox was any less secure than opera, I dunno, I personally find myself feeling a bit safer when somethings open source. Not to mention, I run the no script (disables javascript and now even cross site scripting), ad block plus (remote disabling of banner adds and other popups) and cookiesafe (push click management of all cookies, first and third party). All three of those are easily found in the extensions page for firefox. If your paranoid and want a locked down browser, get all three. :)

---


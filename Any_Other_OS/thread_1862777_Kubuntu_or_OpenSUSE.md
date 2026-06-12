---
title: "Kubuntu or OpenSUSE?"
date: 2011-10-17
forum: Any Other OS
---

### Post by azupan on 2011-10-17
It's that time again... time when new Ubuntu version comes out, time when nothing works anymore, time to consider other distros.
 
I use Linux for mostly for LAMP programming on multi-boot machine. One partition for Windows, one partition for Ubuntu, a small partition for distro testing, an empty bigger partition for new distro if I ever need one.
 
 

Applications I use:
[LIST]
[*]Netbeans & Firefox for PHP programming & debugging
[*]MySql Workbench for database development & administration
[*]MonoDevelop connected to OpenOffice/LibreOffice through UNO bridge to prepare data for the website.
[/LIST]Problems I've encountered:
[LIST]
[*]Firefox is slow beyond useless, burning 100% of **two** processor cores all the time, regardless of what it does.
[*]Mono (partly installed from sources) doesn't work anymore.
[*]MySql Workbench doesn't work anymore, symptoms are similar to Firefox. Pretty much a showstopper.
[/LIST]Probable reason is my current distro, which I've continuously upgraded ever since Maverick, installed and uninstalled all kinds of stuff, and converted from Unity to Kubuntu. Haven't tested everything yet, but it looks like Firefox & Workbench should work OK on fresh Kubuntu installation.
 
I also tried to install OpenSUSE. I'm having problems with GRUB settings, but I believe I can solve that. The reason I'm eyeing OpenSUSE is that the latest Mono versions are deployed on it. Since I'm coming from Windows, programming in Mono is far easier for me than anything else on Linux. Filling database through LINQ is a no-brainer. I have no experience with OpenSUSE, though.
 
So... Which would be better? Kubuntu or KDE OpenSUSE? I'd appreciate any thoughts on that matter.

---

### Post by sffvba[e0rt on 2011-10-17
IMO both will do what you want equally as well (or as poorly)...


404

---

### Post by azupan on 2011-10-17
I've just tested SQL Workbench on fresh Kubuntu installation, and it still doesn't work. So... OpenSUSE it is. Looks like I don't have a choice here.

> **not found said:**
> IMO both will do what you want equally as well (or as poorly)...

Thanks for encouragement.:)  In general, Kubuntu did an adequate job, so, if OpenSUSE is no worse, it should be OK.

---

### Post by doppel.ganger on 2011-10-17
If you decide on openSUSE, don't get it now. The next version, 12.1, comes out in 30 days. [http://www.opensuse.org]("http://www.opensuse.org")

---

### Post by boydrice on 2011-10-17
I am fairly sure that you will always be able to get the latest and greatest mono packages on openSUSE via the mono repo.[http://en.opensuse.org/Mono]("http://en.opensuse.org/Mono"). If you need the latest and greatest KDE openSUSE has repos for that and of course if you want a fairly conservative rolling release the Tumbleweed repo will provide that.  Also zypper is a very underrated tool.

---

### Post by azupan on 2011-10-18
> **doppel.ganger said:**
> If you decide on openSUSE, don't get it now. The next version, 12.1, comes out in 30 days. [http://www.opensuse.org](http://www.opensuse.org)
Yeah, I've noticed that. Unfortunately, I need a working MySql Workbench now. If the only way of upgrading SUSE is by formatting the entire partition, it'll just have to wait a little bit.

---

### Post by MonolithImmortal on 2011-10-18
OpenSUSE has a better KDE implementation to boot.

---

### Post by sffvba[e0rt on 2011-10-18
> **MonolithImmortal said:**
> OpenSUSE has a better KDE implementation to boot.

Not sure how true this is any longer. The last few releases of Kubuntu have really been superb.


404

---

### Post by MonolithImmortal on 2011-10-18
> **not found said:**
> Not sure how true this is any longer. The last few releases of Kubuntu have really been superb.


404

Eh, haven't tried Kubuntu since 10.10. I've read that KDE runs smoother as well on openSUSE, but I don't have any evidence of that.

---

### Post by sffvba[e0rt on 2011-10-18
> **MonolithImmortal said:**
> Eh, haven't tried Kubuntu since 10.10. I've read that KDE runs smoother as well on openSUSE, but I don't have any evidence of that.

Since 11.04 and KDE 4.6 landed I feel Kubuntu is right up there with the best... (and and congrats on hitting 50 posts)... In an hour or so you should have full access to all the options in your control panel...


404

---

### Post by MonolithImmortal on 2011-10-18
> **not found said:**
> since 11.04 and kde 4.6 landed i feel kubuntu is right up there with the best... (and and congrats on hitting 50 posts)... In an hour or so you should have full access to all the options in your control panel...


404

Oh wow, GET OUT OF MY HEAD...

---

### Post by ilovelinux33467 on 2011-10-18
I do prefer openSUSE to Kubuntu for KDE because as well as having nice branding they also offer multiple KDE repositories if you want to upgrade your KDE. They have KDE Updated Apps (Keeps KDE version the same and just updates the KDE apps only), KDE Stable repo (Contains KDE 4.6.0), KDE Release 47 (Contains the latest version of KDE 4.7.x), KDE Release 46 (Contains the latest version of KDE 4.6.x), KDE Factory (Contains KDE 4.7 packages under development) and KDE Unstable SC (weekly snapshots of KDE Trunk). They also have a KDE 3.5.10 repo as well. Though when I tried Kubuntu 10.10 and 11.04 I quite liked them both.

---

### Post by azupan on 2011-10-29
I've installed everything I need (LAMP, Netbeans, Drupal, MySql Workbench etc) on OpenSuse. So far so good. Thanks, everyone! :)

The only thing it doesn't work is Drupal extension on Firefox and OpenSUSE Chromium, but with Netbeans debugger on the server side, I can certainly live with that.

UPDATE: In the latest Chromium update, that, Drupal extension was fixed too. What more could I wish for? :D

---


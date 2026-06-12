---
title: "OS Development and Engineering"
date: 2013-01-19
forum: Any Other OS
---

### Post by UltimateCat on 2013-01-19
;)Hi:

Been learning a lot over the last 2 years about all the different distro's , how unique they are from each other and getting a idea about how these Engineer's and Developers think.

I have been given the privilege of 'Senior Member' in another Linux Forum I belong to and I enjoy helping people. Anyway; the knowledge I have obtain from Ubuntu, Ultimate Edition, Debian and Fedora has lead me to a 
 boat load of questions and the need of a few good references and some guidance.

I'd like to learn more on how many modules make up a kernel; how does a Engineer make patches to the kernel and if a program that is crashing how would I repair/rebuild it. And how to build a Linux driver from source from scratch.

Looking to make a career change from 14 years of Dentistry-

Any help or advice would be greatly appreciated.

---

### Post by BBQdave on 2013-01-20
> **UltimateCat said:**
> Any help or advice would be greatly appreciated.

[**Debian Reference**]("http://www.debian.org/doc/manuals/debian-reference/index.en.html"), [**Fedora Docs**]("http://docs.fedoraproject.org/en-US/index.html"), and the Linux Bible. Great resources to explore, learn, and reference.

I still reference my Red Hat Linux Bible - Fedora/RHEL, from back in the day when Red Hat Linux split into Fedora and RHEL :)

---

### Post by UltimateCat on 2013-01-22
Thanks for the help [BBQdave]("http://ubuntuforums.org/member.php?u=1315974")! :popcorn:

Is it true that if you don't register with RHN that none of the repo's  get configured or activated?

---

### Post by BBQdave on 2013-01-22
> **UltimateCat said:**
> Is it true that if you don't register with RHN that none of the repo's  get configured or activated?

Many years since I have used a purchased Redhat product, but to my understanding of [RHEL]("http://www.redhat.com/"); you sign up, whether it be server or desktop. You pay for a subscription and access to said repos through your RHEL product.

[Scientific Linux]("https://www.scientificlinux.org/") and [CentOS]("https://www.centos.org/") are free versions of RHEL. So through those distros, you could have access to RHEL repos. I have not compared the three distros to see if there are differences - services you receive through paid RHEL vs. Scientific Linux and CentOS.

You can use [rpmFusion]("http://rpmfusion.org/") to access *non-free Libraries* for the above three Linux distros.

In my observation: Scientific Linux and CentOS is to Fedora - as Debian is to Ubuntu. That is to say, Scientific Linux, CentOS, and Debian are long term releases, and Fedora and Ubuntu are more current distros :)

---

### Post by UltimateCat on 2013-01-22
Thanks for telling me about Red Hat and the way it works.
I knew about the subscription but I don't think it's going to work for me.

I have heard about Scientific Linux and CentOS but haven't tried them or compared them. I want to know so I'll do some searches this afternoon.

I have been running Debian on my Desktop since the summer of 2012 and it's a good distro but I seem to like Fedora much more. (less hassle with updates and packages)  But re-installing every 3 to six months isn't exactly what I like to practice regularly- I just do what needs to be done to keep Fedora.

I'll look for Scientific Linux sometime today and check it out.

Thanks again :D

---

### Post by BBQdave on 2013-01-22
> **UltimateCat said:**
> I have been running Debian on my Desktop since the summer of 2012 and it's a good distro but I seem to like Fedora much more. (less hassle with updates and packages)  But re-installing every 3 to six months isn't exactly what I like to practice regularly- I just do what needs to be done to keep Fedora.

I am running F18 with Gnome 3 - smooth and stable system. I understand your thoughts about re-installing. A good practice for longer support: Install annually. F16 will reach EOL soon, so there is time for the few minor bugs in F18 to be patched - between the time F18 is released and F16 goes EOL.

I try to wait a year before the next install, but find myself jumping on the new release :) It is amazing how quickly Fedora patches a new release - with F18, within a day. To be safe though, if you do choose to install a new release every 6 months, wait a couple weeks after it's release.

I keep my data backed up on a home server and portable drive, so I do a fresh install - wiping the HD. After the fresh install, I restore my data and cruise on for another 6 months :D

---

### Post by Cheesemill on 2013-01-22
Or you could switch to a rolling release distro instead.

Since I switched to Arch I haven't had to reinstall once, and I have the latest versions of applications.

---

### Post by UltimateCat on 2013-01-23
> **Cheesemill said:**
> Or you could switch to a rolling release distro instead.

Since I switched to Arch I haven't had to reinstall once, and I have the latest versions of applications.

Good suggestion; Thanks

I have given Arch, Gentoo or Centos a thought-

What does Arch use for a commandline tool; APT or Yum?  Or does it have it's own management tools?

---

### Post by buzzingrobot on 2013-01-23
CentOS and Scientific Linux are recompiled releases of RHEL, with the Red Hat trademarking, etc., removed.

You do not get access to the RHEL repos.  You get access to the CentOS/SL repos.  A pedantic difference, but a difference.

CentOS/RHEL are considerably different than the current Fedora release.  Every so often (every several years, actually) Red Hat takes a Fedora release, tweaks it, etc., and ships it as a new RHEL release.  The current 6.3 release is based on Fedora back around Fedora 12. So, you get Gnome 2, Python 2.6, and other components from that point in time.

The reason for the stability is that they've been fixing bugs since then.

The RHEL kernel identifies as a 2.6 series kernel, but Red Hat backports many improvements and fixes from newer kernels.

CentOS makes for a fine Gnome 2 desktop if you are careful in your choice of repos to acquire the codecs, etc., that are not in the official repos. Current versions of Firefox, Chrome/Chromium/ Thunderbird, etc., are available.  Current versions, especially of multimedia apps, that depend on up-to-date libraries, are probably not available.

RHEL has pretty of good online documentation, so check there before you spend real money to buy something that may turn out to be a reworking of those docs.

---

### Post by buzzingrobot on 2013-01-23
> **UltimateCat said:**
> 
What does Arch use for a commandline tool; APT or Yum?  Or does it have it's own management tools?

Arch uses its own tool, called pacman.

Check out the Arch wiki.  Good learning resource, not just for Arch users.

---

### Post by UltimateCat on 2013-01-28
Thanks [buzzingrobot]("http://ubuntuforums.org/member.php?u=1488460")!

You have been very helpful!:KS

Pacman you say- For Arch 
Does that mean that dependencies will have to be resolved manually?

---

### Post by trent.josephsen on 2013-01-29
pacman does dependency resolution, just like virtually every other package management tool out there. Just because it's not apt or yum doesn't mean it's a relic from 1980.

---

### Post by UltimateCat on 2013-02-04
I'll check out the Arch Wiki; Thank You!

---

### Post by UltimateCat on 2013-02-04
> **trent.josephsen said:**
> pacman does dependency resolution, just like virtually every other package management tool out there. Just because it's not apt or yum doesn't mean it's a relic from 1980.

Never thought of it that way but yeah, your right; thanks

---


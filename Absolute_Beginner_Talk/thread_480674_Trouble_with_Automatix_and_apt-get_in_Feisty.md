---
title: "Trouble with Automatix and apt-get in Feisty"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Jim Shunamon on 2007-06-21
I am trying to run Automatix under Feisty and I keep getting the message "Apt-get is running. Please close apt-get and restart Automatix. How do I close apt-get, and once I do how do I get it started again later?
Thanks all.

---

### Post by bobplano on 2007-06-21
are you running anything like add/remove or synaptic? or anything else that you need root for(you entered your password when you opened it)? automatix is also a sort of package manager so it can't be running at the same time as any other package manager

---

### Post by Nekiruhs on 2007-06-21
Automatix is an unofficial, unsupported installer. The Automatix Devs have requested that all problems with Automatix be posted at their [forums]("http://www.getautomatix.com/forum/"). Furthermore, Automatix is no longer necessary due to the combination of Synaptic, Add/Remove Tool, and Restricted Codec Manager. Also, Automatix has been known to break dpkg causing issues with upgrades and installs. It is recommended that you use the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") methods of installing things in Ubuntu.

---

### Post by arnieboy on 2007-06-21
> **Nekiruhs said:**
> Also, Automatix has been known to break dpkg causing issues with upgrades and installs. 
This is the most popular nonsense in the world of linux these days.

---

### Post by Nekiruhs on 2007-06-21
> **arnieboy said:**
> This is the most popular nonsense in the world of linux these days.
Nonsense as far as you think, It happened to me on  Edgy adn by no means is it fixed in Feisty. I wasn't laughing when I had to spend 2 and a half hours fixing it.

---

### Post by kelvin spratt on 2007-06-21
I'll second that never had a problem with automatix

---

### Post by arnieboy on 2007-06-21
> **Nekiruhs said:**
> Nonsense as far as you think, It happened to me on  Edgy adn by no means is it fixed in Feisty. I wasn't laughing when I had to spend 2 and a half hours fixing it.
2 and half hours to fix what? dpkg? that tells me you have no clue what broke what. Its easy to blame Automatix for one's own newbie mistakes. Most newbies like you believe the FUD spread by rumor mongers who cannot stand Automatix's popularity and never actually take the time to understand what went wrong.

---

### Post by swoll1980 on 2007-06-21
> **arnieboy said:**
> This is the most popular nonsense in the world of linux these days.

Automatix broke my dpkg I had to babysit my pc for 2 hours anwering questions to fix it.

                                                                      [COLOR="Blue"] Automatix[/COLOR]][COLOR="DarkOrchid"]JUST SUCKS[/COLOR]]

---

### Post by arnieboy on 2007-06-21
> **swoll1980 said:**
> Automatix broke my dpkg I had to babysit my pc for 2 hours anwering questions to fix it.

                                                                      [COLOR="Blue"] Automatix[/COLOR]                                                               

                                                                      [COLOR="Magenta"]JUST SUCKS[/COLOR]

and how exactly did Automatix break your dpkg? point me to the relevant source. show me log files, REAL proof that it indeed was automatix and you are not wasting my time and others' by spreading nonsense.

---

### Post by swoll1980 on 2007-06-21
> **arnieboy said:**
> 2 and half hours to fix what? dpkg? that tells me you have no clue what broke what. Its easy to blame Automatix for one's own newbie mistakes. Most newbies like you believe the FUD spread by rumor mongers who cannot stand Automatix's popularity and never actually take the time to understand what went wrong.

Newbie my butt. What are you the automatix fanboy? All I did was tried to install fonts, it got stuck and told me I had to reconfigure dpkg -a

---

### Post by NeoLithium on 2007-06-21
Ok, I think everyone in this thread needs to settle down.  Problems with Automatix need to be directed to their own forums, and not here, as their developers requested, and there's no reason to get angry among other forum posters.

Please guys, lets keep it civil.  If the OP's question has been answered (I haven't seen a reply that it isn't) this thread should be allowed to flow into oblivion.

---

### Post by swoll1980 on 2007-06-21
I thought maybe it was a flook so I tried it again and the same hapend, so automatix broke my dpkg two times, and if it does not brake the dpkg why are there poor souls on ubuntu forums everyday asking how to fix there dpkg because there automatix install got hung?

---

### Post by arnieboy on 2007-06-21
> **swoll1980 said:**
> Newbie my butt. What are you the automatix fanboy? All I did was tried to install fonts, it got stuck and told me I had to reconfigure dpkg -a
If you were installing fonts and "it got stuck", that means apt had a problem. A-P-T, not automatix, OK? Apt is not as robust as most people want to think. A simple power spike can blow out your /var/lib/dpkg/status file and without a fairly recent backup, there is only one way to go: A FULL REINSTALL.
Automatix uses apt as one of its backends, and if apt fails, its not Automatix's fault. We DID NOT write apt. Apt has a million weaknesses and so does dpkg. Apt is an extension of dpkg.

---

### Post by arnieboy on 2007-06-21
> **swoll1980 said:**
> I thought maybe it was a flook so I tried it again and the same hapend, so automatix broke my dpkg two times, and if it does not brake the dpkg why are there poor souls on ubuntu forums everyday asking how to fix there dpkg because there automatix install got hung?
you can install clamav-base on a fresh feisty install. It will break dpkg. Go ahead.. try it. Its just one example of a broken package that Ubuntu hosts and has not managed to fix in 6 months. We at Automatix constantly devise ways to fix Ubuntu issues because we (atleast I) understand dpkg better than most Ubuntu devs themselves.

---

### Post by swoll1980 on 2007-06-21
Automatix just works. Thats funny people say the same thing about Mico$oft

---

### Post by Vorian on 2007-06-21
this thread is out of controll and is now closed

OP, i recommend that you visit the AX forums for support on you problem.

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by bodhi.zazen on 2007-06-21
OK, cool it please.



There is a policy regarding automatix. Please read it.

[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)


I am sorry if you disagree, but please tone down your language.

I do not mind if you advise automatix. I do not care if you use it.

BUT I do mind the tone of this thread.

Please be respectful in your posts. 


=====


Jim Shunamon is asking for help. Please instruct him how to use Ubuntu the "official" way.

You can then direct him to the automatix forums if he would like help with automatix.

---


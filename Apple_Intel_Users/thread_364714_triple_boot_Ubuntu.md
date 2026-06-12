---
title: "triple boot Ubuntu"
date: 2007-02-18
forum: Apple Intel Users
---

### Post by chaosfiredragoon on 2007-02-18
Hi,

I'm pretty new to linux but i have a decent amount of experience with computers.  i'm having trouble creating a triboot on my macbook i've been following the instruction on this website [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu).

i already have both mac osx and window's xp working perfectly.  but when trying to install lilo and the new linux kernel i run into a problem.  when i type in this commmand apt-get install lilo lilo-doc linux-686-smp linux-restricted-modules-2.6.15-23-686 linux-kernel-headers.  i keep getting the error linux-686-smp was not found.  i followed the rest of the guide and linux won't boot of the hard drive so if anyone can tell me what i'm doing wrong please help me.  i'm runing off a 6.06 live cd of ubuntu.  please help me.

---

### Post by groggyboy on 2007-02-18
well, i don't have a mac, but the basics in ubuntu should be the same regardless.

it's very odd that you get an error about the package "linux-686-smp" not being found.  a quick search of [http://packages.ubuntu.com/dapper](http://packages.ubuntu.com/dapper) indicated that such a package *does* exist.

my first question then: do you have a working network connection?  using apt-get on the LiveCD requires this, regardless of whether its dapper or edgy.  seeing as wireless can be tricky to set up, it's easiest if you have a wired ethernet connection (even easier if you connect via a router rather than PPPoE).

open firefox or run "ping www.google.com" from the terminal to check.

once you have working internet, run "sudo apt-get update" in a terminal first, just to be sure apt-get is using the latest packages, then try running the apt-get command you posted.

---

### Post by chaosfiredragoon on 2007-02-18
thanks for your advice.   I'm currently reinstalling linux.  i've checked the internet connection and i am connected i went to google and a few other sites.  I also ran the command sudo apt-get update.  I'm running into the same problem it states that "E: couldn't find package linux-686-smp" when i type in the long command.  I'm currently trying to find a way around this but i'm having no luck.  If anyone else has advice or suggestions please any help is quite welcome.  thank you.

---

### Post by siepo on 2007-02-19
Try the following:
 
aptitude install lilo lilo-doc linux-686 linux-restricted-modules-686 linux-kernel-headers

These linux packages depend on the latest available versions. smp support is already built into the regular kernels, which is why there are no longer -smp versions.

You can use apt-get instead of aptitude, but aptitude seems to be better at resolving dependencies and conflicts, and their syntax is almost the same.

---

### Post by chaosfiredragoon on 2007-03-06
thanks to everyone who posted to try to help.  i found out the problem was that i had a 64bit version of the ubuntu 6.06.  so i dled a copy of 6.06 i386 and burned it followed the guide and poof here i am. I'm currently posting on my linux partition and currently have a triboot on my macbook.  again thanks to everyone that has helped.

---


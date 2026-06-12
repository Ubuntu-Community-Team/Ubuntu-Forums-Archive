---
title: "Questions about Macbook + Ubuntu"
date: 2007-06-07
forum: Apple Intel Users
---

### Post by syalam on 2007-06-07
I am an Ubuntu user but I have it running on my Dell laptop. I am in the market for a new laptop and I would like to try out a Macbook. I have a few questions

1. After dual-booting with Ubuntu what hardware does not work?
2. Why is it worse if I run Ubuntu in a virtual environment?

Thanks.

---

### Post by ronocdh on 2007-06-07
> **syalam said:**
> I am an Ubuntu user but I have it running on my Dell laptop. I am in the market for a new laptop and I would like to try out a Macbook. I have a few questions

1. After dual-booting with Ubuntu what hardware does not work?
2. Why is it worse if I run Ubuntu in a virtual environment?

Thanks.
After some configuration, I can't think of anything that just plain won't work. And as far as running Ubuntu in emulation, it's not really "worse," it's just a matter of preference. For some, options like VMWare Fusion beta 3 are great because they offer side-by-side operation with OS X, whereas other would massively prefer running natively, both for performance and philosophical reasons.

---

### Post by hellomatts on 2007-06-08
However, if you want to use Beryl or other 3d rendering applications, virtualization won't allow you to do so...

---

### Post by ronocdh on 2007-06-08
> **hellomatts said:**
> However, if you want to use Beryl or other 3d rendering applications, virtualization won't allow you to do so...
Very good distinction, sorry for not mentioning this in my post. Hellomatts's completely right. However, this is only in reference to the current generation of virtualization software, and Parallels has announced [it plans to change this]("http://apple.slashdot.org/article.pl?sid=07/06/01/2039253") soon.

---

### Post by kzm. on 2007-06-09
here are my experiences. 
i am really not a linux pro. i use ubuntu now for more than a year now on my old laptop pc and i felt in love with ubuntu. its a wacky old machine which started to overheat lately more and more is huge and heavy, so i bought a macbook c2c.
i installed feisty 64bit, because i read its less going to heat up your hardware.. and hey, its a 64bit processor.

i am semi happy with this buy for following reasons:
1) wireless.
i cant get my wireless working. no idea why. the madwifi doesnt work for me. sometimes it shows up, most of the time not. if it shows up, it shows all the networks but wont connect me to any, even though there is no password or anything needed.
2) mouse
i couldnt get right mouse button through combinations like command+mouse work. i have the f11 or f12 solution now.. but to be honest, the right mouse button is dam important and to go up all the way to the f-button just feels unnatural to me.
3) minors
screen brightness doesnt work for me and i am not sure about my mic neither. isight works. osx boots very, very fast and even programms like eclipse that were damm slow on osx start up faster under osx than ubuntu. so far i had no heat problems much different from osx. i installed smcfancontrol on osx and configured the fan to be minimum present as possible. osx gets hot.. ubuntu gets little hotter. cpu is fine (not at 53% to 100% all the time, but at 1% or 4% with apps open but no interaction). battery is much less under ubuntu.

i am not an os-evangalist, i love ubuntu, but at the end i have to work on this machine. i like linux from an idealistic point of few. i love apt-get and the openess of the system. i also got used to tomboy, gnome-project manager, cash etc... now its (if i at least get wireless working) love against pratical, i guess. ;)

---

### Post by ronocdh on 2007-06-09
> **kzm. said:**
> 1) wireless.
i cant get my wireless working. no idea why. the madwifi doesnt work for me. sometimes it shows up, most of the time not. if it shows up, it shows all the networks but wont connect me to any, even though there is no password or anything needed.
This support changes all the time. If you have a MB C2D, you probably have the Atheros chipset, and so therefore MadWiFi should be treating you well. But just keep trying every update until you get it to work; I've upgraded my MadWiFi before hoping for slightly better reception, only to have it break! A reversion solved this. With the incremental and largely undocumented hardware changes Apple performs on their product lines, you'll just have to stick it out and keep trying to you get a reliable solution. Also, [this post]("http://ubuntuforums.org/showthread.php?t=429641&highlight=widemos+ndiswrapper") is the one I always throw out when people ask about MadWifi here; if widemos's how-to doesn't get you up and running, there's a redaction by Bsantos on page 2 or 3 of the thread.
> 2) mouse
i couldnt get right mouse button through combinations like command+mouse work. i have the f11 or f12 solution now.. but to be honest, the right mouse button is dam important and to go up all the way to the f-button just feels unnatural to me.
Try [this thread]("http://ubuntuforums.org/showthread.php?p=2794622"), and let me know how it treats you.
> 3) minors
screen brightness doesnt work for me and i am not sure about my mic neither. isight works. osx boots very, very fast and even programms like eclipse that were damm slow on osx start up faster under osx than ubuntu. so far i had no heat problems much different from osx. i installed smcfancontrol on osx and configured the fan to be minimum present as possible. osx gets hot.. ubuntu gets little hotter. cpu is fine (not at 53% to 100% all the time, but at 1% or 4% with apps open but no interaction). battery is much less under ubuntu.
I don't really recommend that you alter your fanspeed in OS X, but hey, that's a different deal. You can increase the boot speed of Ubuntu by compiling a kernel specifically for your machine. [This thread]("http://ubuntuforums.org/showthread.php?t=442941") by Dirk.R.Gently may be helpful for you in that regard.

---

### Post by kzm. on 2007-06-10
thanx. i will try those links and let yu know as soon as i did.. thanx a lot, really!

---


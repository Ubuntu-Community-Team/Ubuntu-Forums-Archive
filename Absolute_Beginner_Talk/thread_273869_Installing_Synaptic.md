---
title: "Installing Synaptic"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by reddogzrule on 2006-10-08
Hi,
I am a brand new user to Ubuntu and am still very much a newbie with LINUX in general. I've spent the last two days searching these forums, the Internet, etc for ways to get my Linksys wireless card to be recognized by Ubuntu. This has led me back to getting Synaptic installed, so I can install ndiswrapper (since neither Synaptic or ndiswrapper are installed on the distro I downloaded) and I was hoping I could just get some directions on Synaptic intallation. Everything else here and what I read seems to indicate that it's automatically intalled, but not for me. I see it under "add/remove programs", but it's greyed out and even though I'm an admin user, it won't let me install it. 

Thanks for being patient with me.

Dave

---

### Post by fatsheep on 2006-10-08
It should be located at *System>Administration>Synaptic Package Manager*.  If not try typing this command in the terminal:

> gksudo synaptic

If that doesn't fire up synaptic then it isn't installed and you need to run this command in the terminal to install it:

> sudo apt-get install synaptic

Hope this helps,

-sheep

---

### Post by reddogzrule on 2006-10-08
Thanks Sheep. I tried your commandline inputs, but this is what I got:

gksudo synaptic

bash: gksudo: command not found

sudo apt-get install synaptic

Package synaptic is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.

I actually have Kubuntu insalled, not Ubuntu, but the Kubuntu forum  has very limited resources compared to this one. If you think that Kubuntu is that much different, then I'll go to that one instead.

Thanks.
Dave

---

### Post by jordanmthomas on 2006-10-08
You are looking for a program called Adept instead of Synaptic

It's basically the same, but for KDE

---

### Post by reddogzrule on 2006-10-09
Yes, I see Synaptic listed under Adept, but it's greyed out and won't let me install it for some reason.

---

### Post by reddogzrule on 2006-10-09
I also see KPackage, which is greyed out. Would that install ndiswrapper for me, too? How do I get past the greyed out issue?

---

### Post by dolphinsonar on 2006-10-09
Then you would try:
```
udo apt-get install aptitude
```
for it to work on KDE (KUBUNTU)

---


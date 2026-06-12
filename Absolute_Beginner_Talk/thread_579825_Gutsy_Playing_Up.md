---
title: "Gutsy Playing Up"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Marink on 2007-10-18
I've been running Feisty on this Laptop (a Thinkpad T42) since release and it's been fine, so now I thought I'd do a clean install now that Gutsy is out. So I downloaded the .iso burnt it and installed it, all fine.

But now whenever I try to install something or get something, either via synaptic, terminal or add/remove. It always says that 'whatever' can't be installed and in add/remove it says 'whatever' cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

Anyone know what's going on, on know how to fix it ?

---

### Post by wolfen69 on 2007-10-18
"if it aint broke, dont fix it" (feisty)

---

### Post by lazyart on 2007-10-18
Wolfen69-  If you're not going to add anything helpful, please do not be the first to reply.  It takes the thread out of the "unanswered threads" list and it might get buried.  Many of us who try to help go straight to Unanswered Threads.

Marink,  what are you trying to install?  Maybe you got a bad burn or need to go through the install process again?

---

### Post by Marink on 2007-10-18
> **lazyart said:**
> Wolfen69-  If you're not going to add anything helpful, please do not be the first to reply.  It takes the thread out of the "unanswered threads" list and it might get buried.  Many of us who try to help go straight to Unanswered Threads.

Marink,  what are you trying to install?  Maybe you got a bad burn or need to go through the install process again?

I've tried automatix and vlc as I expected them to work. I installed once with the release candidate and it wouldn't download anything, so I just put it down to a bug, So I downloaded and installed it again today. The official one and yet again it wouldn't pull anything down. It just doesn't want to install anything. 

```
Marink@Marink-Gutsy:~$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  automatix2: Depends: tango-icon-theme-common but it is not installable
              Depends: tango-icon-theme but it is not installable
              Depends: python2.4 but it is not installable
E: Broken packages
marink@Marink-Gutsy:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc
marink@Marink-Gutsy:~$
```

That's what terminal says.
 
Thanks for the help, lazyart.

---

### Post by lazyart on 2007-10-18
Check to see what repositories you have available... I think you may need to enable some of them (vlc for instance, is in universe)

---

### Post by lazyart on 2007-10-18
Also, python is on 2.51, so if automatix wants 2.4 it's not gonna be happy, and ubuntu won't want to downgrade... it might break something else.

---

### Post by Marink on 2007-10-18
Are the repositories the sources list form >System >Admin >Software sources

All I have in there is [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) and [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt).

What are the universe ones ?

Thanks again btw.

---

### Post by lazyart on 2007-10-18
On the first tab go ahead and enable the first four boxes (main, universe, restricted, multiverse).  That will give you all the goodies.  Then try to apt-get those files again.  You may still have a problem with automatix if it hasn't been repackaged for Gutsy, but I know next to nothing about that package.  I believe they have their own site for support.

---

### Post by ajgreeny on 2007-10-18
I suggest you forget about automatix2 and use the repos available for ubuntu, including medibuntu for some of the multimedia packages if you want to.  Automatix has been known to present a number of problems in several of the versions of ubuntu and is best left to those who really know what they are doing, rather strange when automatix is meant to make things easier for the new user to get things they can't find in the repos.

I've used medibuntu repos since they were available (can't remember the version of ubuntu) and not had any difficulties with it at all.

---

### Post by Marink on 2007-10-18
Thankyou thankyou thankyou so much for your help. It's all working now, and I can finally get to work. No idea why they weren't enabled by default.

Thankyou again, and I will use mediabuntu.

---


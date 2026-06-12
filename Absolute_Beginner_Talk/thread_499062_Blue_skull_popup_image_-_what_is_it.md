---
title: "Blue skull popup image - what is it?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by gwicks on 2007-07-12
Hi all,

This is going to sound very strange...   Has anyone ever seen or had a "sinister blue skull" image flash up on their system while browsing?  To be honest, it's freaked me out!


I have a Dell 610 Laptop with 7.04 installed (next to a Vista installation - work) that I use when at home to browse the internet (Firefox 2.0.4).  I connect via a wireless network.

Yesterday, sat at home and browsing various sites (youtube, slashdot etc) and then, for two seconds, the whole screen changed to a large blue skull! (think of Skeletor's head from Masters of the Universe) with white eyes on a black background.  There was a quick series of "telephone like" tones that came from the speakers.

This came up for about 2 seconds, and then disappeared, back to the browser.  After I recovered (as I said it freaked me out - I really thought I'd imagined it), I did a bit of googling for 'blue skull' but zip found.  But about 20 mins later, it did it again!  

Now I'm getting worried.  Is it some virus / worm / trojan?  I've always trusted Ubuntu / Debian as a "safe from viruses" environment, but maybe I'm being nieve (sorry for the spelling)  Or is this a normal (but freaky) error message / system error (but surely it would be documented!)

It's a fairly new installation, normal repositories (added Oracle for OracleXE and vmware for vmware server).  

Thanks in advance - Guy

---

### Post by smoker on 2007-07-12
i sincerely doubt it is a virus, but i would clean out your cookies and cache in firefox to see if that puts an end to it.

---

### Post by sailor2001 on 2007-07-12
it's a warning to stop smoking................:)

---

### Post by gwicks on 2007-07-12
Clearing firefox out was done!

The fact that it took over the whole screen makes me doubt it was firefox itself.  The first time, I can't really remember, but I think I just had the laptop on my lap without touching it with my hands cause I was drinking coffee.  (Oh the mess I made!) 

The second time it happen was when (coincidence?) I'd clicked on an icon on the top menu bar (updates ready - the open office stuff from yesterday).

---

### Post by gwicks on 2007-07-12
sailor2001 - LOL!  I wish!

---

### Post by smoker on 2007-07-12
is this it? it is a 'myspace' layout.

---

### Post by EdThaSlayer on 2007-07-12
I would like to have something like that pop-up. Where can I get it? :P
lol, just kidding, but it would be interesting to try it out for once.

---

### Post by Durden10 on 2007-07-12
Sounds nice ;)
But this shouldnt be a regular virus, maybe someone installed a program as a joke?

---

### Post by gwicks on 2007-07-12
> **Durden10 said:**
> Sounds nice ;)
But this shouldnt be a regular virus, maybe someone installed a program as a joke?

No-one else has access to the laptop.  

I did start to (crudely) monitor CPU and network for any "webbot like" activity - didn't see anything...

---

### Post by mlentink on 2007-07-12
> **gwicks said:**
> No-one else has access to the laptop. 
You connect via wireless. How well secured is that?

---

### Post by 3rdalbum on 2007-07-12
This sounds highly strange. You should probably install rkhunter and chkrootkit and run them, and also KlamAV.

I would also double-check what services are running on my system that might have open ports, and what repositories are active. There was a repository a little while back that was really for personal use, and all sorts of other people started using it, so the administrator put up a new package that changes the desktop background to a skull. Of course, the people who used the repository noticed a new version of whatever the package was, and upgraded, and got the skull.

---

### Post by gwicks on 2007-07-12
[ahem / *cough*]  Technically, it's not my wireless...  Let's just say that, from my couch, I have a signal from a poorly configured network in the local [leech! you scream] ;)

I assume, that although the wireless signal is open, the laptop is secure because of the inherent robustness of Linux / Ubuntu.  This is exactly why I DONT use my work Vista installation at home on this network.

---

### Post by mlentink on 2007-07-12
> **gwicks said:**
> Let's just say that, from my couch, I have a signal from a poorly configured network in the local
Poorly configured as in ´no encryption' ?

> **gwicks said:**
> I assume, that although the wireless signal is open, the laptop is secure because of the inherent robustness of Linux / Ubuntu.
I sincerely hope you do not use passwords on websites that are the same as your user account? Or login to remote services with such a password? Your system is only as robust as you make it. Usually all doors are locked, but if you choose to give someone a key...

---

### Post by RRS on 2007-07-12
> **gwicks said:**
> [ahem / *cough*]  Technically, it's not my wireless...  Let's just say that, from my couch, I have a signal from a poorly configured network in the local [leech! you scream] ;)

I assume, that although the wireless signal is open, the laptop is secure because of the inherent robustness of Linux / Ubuntu.  This is exactly why I DONT use my work Vista installation at home on this network.

There's some tutorials floating around the web on "fun" things to do when someone discovers an outside user (in this case,you) accessing their wireless connection.

I seem to recall they can involve the sort of thing you've experienced instead of simply reconfiguring the network.

---

### Post by gwicks on 2007-07-12
> **RRS said:**
> There's some tutorials floating around the web on "fun" things to do when someone discovers an outside user (in this case,you) accessing their wireless connection.

I seem to recall they can involve the sort of thing you've experienced instead of simply reconfiguring the network.

Without making the thread a comment on the moral's of using an unsecured wireless ('cause I'm guilty as sin!) - I don't think the owner of the wireless would be technically competent enough to try anything nearing "fun".

When browsing I use disposable passwords - and the sites are not sensitive at all.  If (and only rarely and if) I use a secure webVPN to access work.

---

### Post by gwicks on 2007-07-12
> **3rdalbum said:**
> This sounds highly strange. You should probably install rkhunter and chkrootkit and run them, and also KlamAV.

I would also double-check what services are running on my system that might have open ports, and what repositories are active. There was a repository a little while back that was really for personal use, and all sorts of other people started using it, so the administrator put up a new package that changes the desktop background to a skull. Of course, the people who used the repository noticed a new version of whatever the package was, and upgraded, and got the skull.

Thanks - I'll try this and let you know...

---

### Post by smoker on 2007-07-12
> **gwicks said:**
>  - I don't think the owner of the wireless would be technically competent enough to try anything nearing "fun".

he may know someone who does though, or another user of his computer may know!

---

### Post by mlentink on 2007-07-12
> **gwicks said:**
> Without making the thread a comment on the moral's of using an unsecured wireless ...

Sorry, I didn't want to start such a discussion at all. 
The only thing I wanted to point out is that while you may think your computer is secure, if you communicate over the air waves, anybody can pick up what your are doing. Without security measures, WLAN is inherently unsafe, at any speed. Feind hört mit...

---


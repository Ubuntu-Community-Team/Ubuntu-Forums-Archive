---
title: "wireless connection loss results in gusty crash"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by l0stendeavor on 2008-01-03
Every couple days or so my network manager losses wireless connection. In trying to reaquire the singal the nm-aplet freezes and so does the rest of my system. I'm unable to shutdown normally or open any programs. I can however run some things that are already open. If i have the terminal open at the time I can run the shutdown command but halfway through it stops and gives me this message

```
NetworkManager: <warn> nm_signal_handler(): Caught Signal 15, shutting down normally
```

Then it proceeds to freeze and forces me to hard reboot. This problem has me stumped and I'm worried about data corruption and hardwar failure from shutting down my computer like that. Any ideas/suggestions about what could be causing this would be excellent.

---

### Post by mandrill on 2008-01-03
Would have to know more - what hardware & wireless card, etc.......there is a link at the beginning of the forums for known compatible cards and even the idiosyncrasies of some of them when used with Ubuntu. Gutsy's wireless drivers are actually pretty good (for Linux).

---

### Post by l0stendeavor on 2008-01-03
i thought I had included those details but I'm running 7.10 on a dell 1420n with Intel® PRO/Wireless 3945 internal Wi-Fi

---

### Post by mandrill on 2008-01-03
that machine (inspiron notebook) can be ordered with ubuntu oem - is that what you have?

---

### Post by l0stendeavor on 2008-01-03
it came with 7.04 but then I did  fresh install of 7.10

---

### Post by mandrill on 2008-01-03
> **l0stendeavor said:**
> it came with 7.04 but then I did  fresh install of 7.10

Just a guess here, but did you activate all the repositories? madwifi is now available thru synaptic - a quick search will tell you if it is installed - I use a netgear wpn311 card, that was poor at best on 7.04 and works fine on 7.10 now.....(wpa)....also, when you click the nm-applet, do you see other networks? You might check your restricted drivers under system>admin>restricted drivers.....I know these are just the basics, and you probably have done them already, and I certainly do not wish to demean in any way your expertise...just ckeckin' :)

Checked around a little - this seems to be a known bug, but all bugs (most) have workarounds. Intel's driver site for your wifi has some info about linux driver downloads.

---

### Post by l0stendeavor on 2008-01-03
I uncommented all my repositories after installtion so I have those. As for my nm-applet I can see all the networks its just that once my connection drops and I try to reconnect it the whole system locks up. I have my restricted-modules installed which contains madwifi. 

Is this a known bug for my intel drivers or what?

---

### Post by mandrill on 2008-01-03
> **l0stendeavor said:**
> I uncommented all my repositories after installtion so I have those. As for my nm-applet I can see all the networks its just that once my connection drops and I try to reconnect it the whole system locks up. I have my restricted-modules installed which contains madwifi. 

Is this a known bug for my intel drivers or what?

Yes, there have been some problems. Try sudo apt-get install linux-restricted-modules, unless you already have.....another trick that might work is to hardwire your machine, and do sudo apt-get update, using all repos, or do it from the GUI. (I bet a clean install would fix everything!)


Here is a link to same driver discussions  

[http://ubuntuforums.org/archive/index.php/t-578885.html](http://ubuntuforums.org/archive/index.php/t-578885.html) 

And this from same page

"I had many problems with the 3945ABG. Then I read a post to disable the ipw3945 driver and enable the iwl3945. Since then, wlan is working very well"

Either way, post the results for the rest of us to learn by as well!

---

### Post by l0stendeavor on 2008-01-04
I purged my linux-restircted-modules and then  used apt-get to redownload in the hopes it was just a broken package. I will wait a  couple days to see if the problem persists then i might have to perform a fresh install, although I would prefer not to.


I'm still losing connection but my system is no longer freezing up in conjunction wiht loss of connection. Will try a new network manager see if that does the trick.

---

### Post by jimmy the saint on 2008-02-19
I am having the exact same problem!!  we have a thread going regarding this with no success so far here [http://ubuntuforums.org/showthread.php?t=694949]("http://ubuntuforums.org/showthread.php?t=694949")
Did you solve it?

---


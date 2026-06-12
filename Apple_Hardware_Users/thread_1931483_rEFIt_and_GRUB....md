---
title: "rEFIt and GRUB..."
date: 2012-02-25
forum: Apple Hardware Users
---

### Post by dakos on 2012-02-25
Is there a way make rEFIt to tell GRUB which OS to load without telling GRUB again or would something like that need to be hard coded into both?

---

### Post by musicman10489 on 2012-02-28
In your terminal type
```
$ sudo nano /etc/default/grub
```

Arrow down to the line 
```
GRUB_TIMEOUT=10
```
and change it to
```
GRUB_TIMEOUT=0
```

Next, hit CRTL+O (that's an uppercase o, not a zero) and then Enter/Return. Then hit CRTL+X. Now type into your terminal 
```
$ sudo update-grub
```

That's it! Hope this helped and if it did, don't forget to mark the thread [SOLVED] :)

---

### Post by dakos on 2012-02-29
Thank you for the reply musicman :)
What you suggest is just tricking GRUB to take the first choice on the menu and not giving any booting choice to the user which is fine if you're on a dual boot system (OSX, Ubuntu), this isn't a good solution for triple boot where you want to boot a different OS using GRUB (Windows or Ubuntu and OSX, the latter doesn't need GRUB), my question is wether it's possible to use rEFIt to let GRUB know which OS I want to boot and not have to choose the same thing twice...

---

### Post by musicman10489 on 2012-02-29
Ahhh I see what you're saying now. I have limited knowledge concerning triple boots and the such but I'll still see if I can come up with some useful info for you.

---

### Post by varunendra on 2012-03-01
Sorry for a no-help post, but I couldn't help commenting..

*@musicman10489,*
When you only post some codes that override default settings, it may sometimes lead to results that may be undesirable to the original poster. So you should always consider explaining their effect (as a warning or a short comment) whenever you make such suggestions.

You seem to be willing to help here, but setting grub timeout to zero, regardless of the system being dual or triple (or even more) boot, is never recommended since afterwards, you'd be left with no easy way to choose the other OS unless you re-edit the grub-defaults file (or grub.cfg itself).

Please don't take it as a criticism, it's just a friendly advice; I've made such mistakes myself in the past. :)

*@dakos*
Sorry once again for being off-topic. I have no idea about rEFIt or how it interacts with grub, so can't offer any direct help with that. But this guide seems to offer what you are asking for: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
(pay attention to "[Avoid long EFI wait before GRUB]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Avoid_long_EFI_wait_before_GRUB")" part)

---

### Post by dakos on 2012-03-01
Dear varunendra,
Thank you for the suggestion, I've read the linked page about five times even before I started the install (even edited it and quite a few others), I usually set the GRUB timeout to 1-2 seconds and with this configuration my MacBook boots in less then 30 seconds to every OS I choose so no need to bless any partition.

May be someone knows how GRUB and rEFIt interact?
Thank you again

---

### Post by musicman10489 on 2012-03-01
*@varunendra*
I sincerely appreciate your advice. That never even occurred to me to just explain what everything does. I am definitely going to be a lot more thorough with my posts from now on. Thanks for being so kind about it instead of just jumping down my throat :)

---


---
title: "[SOLVED] Do I need a firewall within VMWare?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by brett611 on 2008-02-18
Hi,
I have Gutsy as my full install, using Firestarter and ClamAV.  I just installed VMWare with WinXP.  Do I need to install a firewall within VMWare, like ZoneAlarm?  I'm connecting to the internet in my VMWare session via NAT, so I assume the answer is 'no', but you know what happens when you assume

The only reason I'm using VMWare is because MS Money and TurboTax don't work with Wine.  Given that these are using/storing highly sensitive financial data I want to be certain.[please don't suggest alternatives for these, tried em and don't like em.  thanks though]

Ditto questions for antivirus, spyware

Thanks!

---

### Post by justleen on 2008-02-18
No :)

(besides, its a VM! make a snapshot, and if all else fails, place it back..)

Edit: spy / malware and viruses can be a problem on a VM..

---

### Post by randy78 on 2008-02-18
I run XP as a Virtual Machine through VirtualBox and I have Comodo Firewall and Avast installed on it...

I have Firestarter on my Gutsy install and that takes care of pretty much everything, but still, in the XP Virtual Machine, I like to have Comodo running so I can control which apps are allowed to connect to the Internet (WGA, Automatic Updates, etc... )

Keep in mind that Comodo won't prevent any of your Linux apps from connecting to the web, and as I said, I just use it for reigning in prog's on the XP side ;)

---

### Post by brett611 on 2008-02-18
Thanks.  I used Comodo and Avast in my pre-Gutsy days.

---


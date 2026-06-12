---
title: "Internet Security???"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by troica on 2006-06-12
Hello, I'm really really new in Ubuntu, actually LINUX too.
I've installed Ubuntu 6.06 LINUX first time ever.
Installation went perfect without any problem, very impressive!
For few days, I've been trying to figure out the system, the difference from Windows, etc....Ubuntu is very nice and easy to learn and everything so far is just fine.
Only one thing came up in my mind.
What about Internet Security?
As you know, in Windows, Firewall, Virus, Spyware, etc are big problem, so we have to install software to protect...like McAffe, Norton.
We don't have to do that in Ubuntu?
Or, is there some software to install?

Thank you for your reply......Troica

---

### Post by rado_london on 2006-06-12
The only thing you really need is firewall. Look for Firestarter. But if you are behond router you can live without it. Everything else is useless for linux as it is safe out of the box.

---

### Post by u.b.u.n.t.u on 2006-06-12
What rado_london said  is spot on. I just use firestarter. The other things you mentioned are part of the Windows world, not the Linux world.

---

### Post by nanotube on 2006-06-12
see the third link in my sig (the faq), and find the question about firewall and antivir 

(as you may guess, you are not the first one to be asking this question) :)

---

### Post by troica on 2006-06-13
Well, since I don't have to worry about, I'll look for Firestarter later.
Thank you very much...Troica

---

### Post by Raavea on 2006-06-13
Never under-estimate your enemy, or over-estimate your troops.

 In this case, whilst linux in general is much less at risk than a windows distro *(I read an article where a broadband-enabled copy of XP on a fresh PC, normal browsing, was riddled with malware within twenty minutes. That's with absolutely no protection...)* it is not true to say it's 'safe' out of the box.

 To be sure, it's more inhosiptable to malware, but there is malware out there. On the whole, I believe it is because linux users tend to be more aware that hackers don't bother. That and the big money lies in the pay-for world of MS.

 So, whilst yeah I'd say firestarter is all you'd need, it'd be a good plan to get avast! for linux and scan once a month, just in case. :)

---

### Post by johnnymac on 2006-06-13
It's funny to hear people say "Oh linux - you don't need antiv"

And I say - "Until the day you wish you had it"

You typically needs 3 things with any system - at a minimum:
1.  Firewall of some-sort
2.  Antivirus just for that rainy day...
3.  Rootkit hunters

History shows us that, true, Linux doesn't have big issues with viruses.  BUT, when you do get one it's a friggin doosie!  So don't be silly - put it on there it isn't going to hurt you.  Also, if you are a file-sharer and do the P2P stuff you better invest time in setting yourself up a rootkit hunter, chkrootkit is a good one.  Otherwise you'll find yourself logging into a system that no-longer allows you to log in and has become some evil monkey-hackers zombie beeotch.

Regardless.....it's fun to install and set stuff up :)

GL

---

### Post by weasel fierce on 2006-06-13
If you share or email files, you will also want to consider anti-virus, to avoid passing along something unpleasant.

---

### Post by maddbaron on 2006-06-14
how doInstalling from RPM
===================

To install avast4workstation from RPM package, login as root and type
  rpm -Uvh avast4workstation-*.i586.rpm
(replace * with the version of your RPM package).


Installing from tarball
=======================

No installation is required, files in the bin/ can be run directly after
unpacking the .tar.gz archive. If you would like to integrate avast! into 
your KDE or GNOME desktop, run 
  
  ./lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh install
  
from the place where you unpacked the archive. Run
  
  ./lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh uninstall

to uninstall previously installed menu entries.

Please see the README file and man pages for more information how to use
the program. i install avast! i downloaded the tg file and unzipped it and brought the folder into another folder. what next?

> 

what is tarbell? 

the file is in my maddbaron folder. how do i use this tarbell to operate it?

---


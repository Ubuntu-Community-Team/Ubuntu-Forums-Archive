---
title: "Lucid lynx emac internet predicament....."
date: 2011-01-24
forum: Apple Hardware Users
---

### Post by Jarbuntu on 2011-01-24
So I just installed ubuntu from a net install, and updated from the internet and posted on this site through firefox while installing vlc wich just froze at 90%.....

but when I try to add community repos it comes up with errors. And while running a system check it says I have no internet connection...

I'm connected through ethernet on a router wich works with the g5 in the other room running osx, and the pc upstairs running ubuntu meerkat. Now I had this same problem with SUSE 11.1 and worked around it by adding through terminal but I was never able to add from the GUI.

Any ideas?

---

### Post by BlastXng on 2011-01-30
> **Jarbuntu said:**
> So I just installed ubuntu from a net install, and updated from the internet and posted on this site through firefox while installing vlc wich just froze at 90%.....

but when I try to add community repos it comes up with errors. And while running a system check it says I have no internet connection...

I'm connected through ethernet on a router wich works with the g5 in the other room running osx, and the pc upstairs running ubuntu meerkat. Now I had this same problem with SUSE 11.1 and worked around it by adding through terminal but I was never able to add from the GUI.

Any ideas?

Jarbuntu.. Are you using DHCP or Static IP on your machine? One thing that I have found is that if I hard code the IP Address (static that is) the networking tends to work better.. 

Secondly, are you using wireless or 10/100BaseT connections? If using Cat5 (10/100) you may want to check the cabling and the switch port, even the switch for that matter that you are connected to. 

Also I have found that with PPC and Ubuntu, you may have issues or misses with repos cause I haven't found too many of them out in the world only on a few select locations, which sucks of course. 

So I'd suggest setting a static IP if you can first of all.
Check the cabling, ports, etc. next 
Double check the Repositories that you are pointing to for PPC.

---


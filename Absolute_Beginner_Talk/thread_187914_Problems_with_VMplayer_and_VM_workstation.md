---
title: "Problems with VMplayer and VM workstation"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by hotstovejer on 2006-06-03
Just got my dapper install working great! (I love it!) I am trying to set up the whole VMware dealie for the times I want to brutalize myself with a windows install of my choice.

I installed player, but didn't know that I had to create an image of the os to run it. So I went and got workstation, but when I go to install it, it tells me.

hotstovejer@cutiepie:~/vmware-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

Now, I understand what that means (kinda), but do I need to uninstall VMPlayer then install Workstation? What are the steps I need to take to uninstall VMPlayer?

Just a little offbase, and I thought I was doing well when I got all the graphics stuff to work!

Any help would be appreicated.

Jeremy

---

### Post by Rackerz on 2006-06-03
I think you need to uninstall the player first then try it. I had the same problem, but no solution.

---

### Post by hotstovejer on 2006-06-03
[QUOTE=Rackerz]I think you need to uninstall the player first then try it. I had the same problem, but no solution.[/QUOTE]

There lies the problem... how do I uninstall the player?

---

### Post by Rackerz on 2006-06-03
Go into Synaptic and search for vmware, check if the player is installed.

---

### Post by mrtisoy on 2006-06-04
I had to run this script to uninstall my vmplayer:

```
 sudo /usr/bin/vmware-uninstall.pl
```

---


---
title: "Upgrading with no cd"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Axis on 2007-04-23
I was interested in upgrading from version 6.06 to fiesty fawn (7.04). However I can't seem to figure out how, without a fresh install with a new cd. Is it possible to do this without? Thanks alot,

Axis

EDIT: However its probably too late. I just realized that I must have version 6.10. How do I go about getting to that version?
EDIT AGAIN: Yes, double editing. I just want to note that it is not listed as an option to update from 6.06 to 6.10 in the update manager list.

---

### Post by Gazneth on 2007-04-23
I am upgrading my laptop right now, seems to me you would be better off backing up /home and doing a fresh install of 7.04.  My laptop has been churning for over 2 hours versus a fresh install of maybe 15 minutes.  Lappy is a core duo w/ 1gig ram. When I update my desktop after some testing I will definitely do a fresh install.

---

### Post by Axis on 2007-04-23
> **Gazneth said:**
> I am upgrading my laptop right now, seems to me you would be better off backing up /home and doing a fresh install of 7.04.  My laptop has been churning for over 2 hours versus a fresh install of maybe 15 minutes.  Lappy is a core duo w/ 1gig ram. When I update my desktop after some testing I will definitely do a fresh install.

Fresh install isn't an option. I was given a copy of ubuntu because I don't have a cd burner at hand.

---

### Post by Gazneth on 2007-04-23
I think this is the correct code to upgrade to 6.10. In a terminal type ```
sudo apt-get update
```
```
sudo apt-get upgrade
```
It has been some time since I did this so search the forums to see if I am correct.

---

### Post by LaurelLynn on 2007-04-23
Dear Axis,

One thing I have seen in the official guides, is that you should not try to go strait from Dapper -> Fiesty. Instead you go Dapper -> Edgy -> Fiesty.  And the community docs on this site has guides to each upgrade.

---

### Post by Gazneth on 2007-04-23
Sorry that was the wrong code for the terminal, that only upgrades packages with available upgrades. This is from the community site
```
gksu "update-manager -c" 
```

---

### Post by Axis on 2007-04-24
I found out how to get there (however it didn't help at all, I can just do that through the gui)

However it says there are no updates available, which dosen't seem to really be possible...

---


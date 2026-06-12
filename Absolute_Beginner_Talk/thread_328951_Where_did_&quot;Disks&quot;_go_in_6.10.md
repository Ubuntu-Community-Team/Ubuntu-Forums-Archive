---
title: "Where did &quot;Disks&quot; go in 6.10?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Bartender on 2006-12-31
In 6.06 under System>Administration the second option was Disks, or something similar, that allowed you to look at the disks & partitions.
6.10 doesn't have that.  I caught a post yesterday that said to go into Alacarte but everything that can be checked under "Administration" already is.  
I'd just assumed that this was taken out in Edgy, although I missed it.  If it's still in there somewhere how do I get it back?

---

### Post by macogw on 2006-12-31
I don't know, but I want it back.

---

### Post by jimrz on 2006-12-31
> **Bartender said:**
> In 6.06 under System>Administration the second option was Disks, or something similar, that allowed you to look at the disks & partitions.
6.10 doesn't have that.  I caught a post yesterday that said to go into Alacarte but everything that can be checked under "Administration" already is.  
I'd just assumed that this was taken out in Edgy, although I missed it.  If it's still in there somewhere how do I get it back?

you can see your disks in "System Monitor" or Gparted, both also under System > Administration. I, too, would like to see "disks" reinstated

---

### Post by BLTicklemonster on 2006-12-31
sudo aptitude install psydm 

Not the same but it works.

---

### Post by macogw on 2006-12-31
I'm not on the live cd right now, but when I go to my system monitor, only / shows up.  Swap doesn't.  Though when I type "free" it keeps telling me I have zero swap even though I know I have 2 gb.  I can't figure out why.

---

### Post by jimrz on 2006-12-31
> **macogw said:**
> I'm not on the live cd right now, but when I go to my system monitor, only / shows up.  Swap doesn't.  Though when I type "free" it keeps telling me I have zero swap even though I know I have 2 gb.  I can't figure out why.

in system monitor swap shows up in the "Resources" tab right below memory usage, not with the others partitions in "File Systems"

---

### Post by macogw on 2006-12-31
Swap says 0 bytes of 0 bytes.  It also doesn't see 22 mb of my RAM... weird.  If I boot from a 6.06 disc and go to the Disks thing it shows my swap as existing though.

---

### Post by bulldog on 2006-12-31
Is the swap properly listed and mounted in your fstab?

---

### Post by BLTicklemonster on 2006-12-31
Oops, that's 

pysdm


not psydm :)

---

### Post by MkfIbK7a on 2006-12-31
in kubuntu you can use kinfo to look at that and all other hardware

---

### Post by steve.horsley on 2007-01-01
> **BLTicklemonster said:**
> Oops, that's 

pysdm


not psydm :)

Hey, I like that. It should be in the default install. You need to get rid of that UUID stuff, but that's no loss.

---

### Post by BLTicklemonster on 2007-01-01
Pay careful attention to your fstab. If anything weird happens, use fstab~ to get your drives back to read/write. 

Not sure if pysdm did it, but I remember something strange happening first time I tried using it.

---

### Post by matthew on 2007-01-01
I'm interested in a definitive answer to the OP's question as well. I will take a guess that the devs probably thought "Disks" was redundant since baobab is now included by default (called Disk Usage Analyzer in Applications->Accessories). I will echo the sentiments that the option would be nice to have back.

---

### Post by smoker on 2007-01-06
[QUOTE][I'm interested in a definitive answer to the OP's question as well. I will take a guess that the devs probably thought "Disks" was redundant since baobab is now included by default (called Disk Usage Analyzer in Applications->Accessories). I will echo the sentiments that the option would be nice to have back./QUOTE]

i would like to see this back myself (have just upped to edgy). i have tried looking for it in the repositories, does anyone know where/if it is available?

(hme! quote from Mathew, post13)

---


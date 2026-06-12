---
title: "wipe hard drive"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-02-02
okay is there anyway that i can wipe a hard drive of everything so i can have a nice clean hardrive?

---

### Post by alfinahopwas on 2008-02-02
> **fedex1993 said:**
> okay is there anyway that i can wipe a hard drive of everything so i can have a nice clean hardrive?

Thats a good question when you find out please let me know.. Thank you.  :popcorn:

---

### Post by logos34 on 2008-02-02
[Darik's Boot and Nuke]("http://dban.sourceforge.net/") or [Active KillDisk]("http://www.google.com/url?q=http://www.killdisk.com/downloadfree.htm&sa=X&oi=smap&resnum=1&ct=result&cd=1&usg=AFQjCNHcQh0uFe2NfxCOtKHMcX57GZrCPQ")

---

### Post by Bachstelze on 2008-02-02
> **logos34 said:**
> [Darik's Boot and Nuke]("http://dban.sourceforge.net/") or [Active KillDisk]("http://www.google.com/url?q=http://www.killdisk.com/downloadfree.htm&sa=X&oi=smap&resnum=1&ct=result&cd=1&usg=AFQjCNHcQh0uFe2NfxCOtKHMcX57GZrCPQ")
A good

```
sudo dd if=/dev/zero of=/dev/sda
```

does it just as well ?

---

### Post by fedex1993 on 2008-02-02
okay thanks half to celar off my dads laptop his work screwed around with it

---

### Post by fedex1993 on 2008-02-02
> **HymnToLife said:**
> A good

```
sudo dd if=/dev/zero of=/dev/sda
```

does it just as well ?

it has a windows partition on it because it his works laptop and they messed up on the install of windows xp and i am wiping the hard drive so they are forced to reinstall it

---

### Post by Crumpets and Jam on 2008-02-02
> **fedex1993 said:**
> okay is there anyway that i can wipe a hard drive of everything so i can have a nice clean hardrive?

Do you want a fresh installation of Ubuntu? Insert the Live CD or the Alternate CD that you can download and install it following the instructions. When prompted, select 'Guided - Use Entire Disk'. This will wipe everything on your hard drive and leave you with a nice fresh Ubuntu installation.

---

### Post by randy78 on 2008-02-02
> **Crumpets and Jam said:**
> Do you want a fresh installation of Ubuntu? Insert the Live CD or the Alternate CD that you can download and install it following the instructions. When prompted, select 'Guided - Use Entire Disk'. This will wipe everything on your hard drive and leave you with a nice fresh Ubuntu installation.

I agree... unless you have some pretty sensitive information on the disk, it's best to just save some time and do this.:)

---

### Post by logos34 on 2008-02-02
> **HymnToLife said:**
> A good

```
sudo dd if=/dev/zero of=/dev/sda
```

does it just as well ?

Yep.  I'm a fan of the dd command for other things...elegantly simple.  I recommend DBan out of habit.  Maybe I'll just suggest dd from now on.

---

### Post by fedex1993 on 2008-02-03
> **logos34 said:**
> Yep.  I'm a fan of the dd command for other things...elegantly simple.  I recommend DBan out of habit.  Maybe I'll just suggest dd from now on.

okay well it has windows installed will the dd command work. also how can i become root while on a live cd?

---

### Post by user1397 on 2008-02-03
> **fedex1993 said:**
> okay well it has windows installed will the dd command work. also how can i become root while on a live CD?no that command is a linux command; it won't work in windows.  you must insert the live cd and boot to it to perform that command.  you could also just go to system > administration > G Parted Partition Editor while on the live CD and delete all partitions there to wipe your hard drive clean (pretty strait forward, if you don't like command lines)

The Live CD is root by default.

---

### Post by fedex1993 on 2008-02-03
yeah i know i am booting from a live cd sorry forgot to mntion that

---


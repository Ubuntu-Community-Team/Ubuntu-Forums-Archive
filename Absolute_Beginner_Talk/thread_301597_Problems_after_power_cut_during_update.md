---
title: "Problems after power cut during update"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Count de Monet on 2006-11-17
Hi

I was auto installing updates after my very first installation of Ubuntu when I suffered a power cut.

After the power was restored and the machine re-booted i tried to continue with the upgates. I was told to run 'dpkg --configure -a' so I ran 'sudo dpkg --configure -a' but got the following error::( 

dpkg parse error, in file ` /var/lib/dpkg/updates/0001 ' near line 22 package `gimp': EOF after field name`'

How do I proceed and continue with the update or re-download the whole update package again.:confused: 

Thanks

The Count

---

### Post by Bachstelze on 2006-11-17
Try *apt-get -f install*.

---

### Post by Count de Monet on 2006-11-17
Ok, did that and got:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by ajgreeny on 2006-11-17
You need to run apt-get as root so try *sudo apt-get -f install.*

---

### Post by recrispi on 2006-11-17
> **Count de Monet said:**
> Ok, did that and got:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Hi!
did you wrote 

sudo apt-get -f install

That should help you with the "are you root?" question.

I got this problem some time ago and in my desperation I searched for a lock file in the apt directories (don't remember well, but it must've been something like /var/cache/apt) and simply removed it as root. and the I could continue with instalation. It was a brute force solution, but I didn't have time to search for a more elegant solution.

I hope this helps.

---


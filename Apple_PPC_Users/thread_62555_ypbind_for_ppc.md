---
title: "ypbind for ppc"
date: 2005-09-05
forum: Apple PPC Users
---

### Post by sobers_2002 on 2005-09-05
hi i can't seem to search it through apt

how do i get rpm for it?? i really really need it .


thanx in advance
Saurabh

---

### Post by king_arthur on 2005-09-09
[QUOTE=sobers_2002]hi i can't seem to search it through apt

how do i get rpm for it?? i really really need it .


thanx in advance
Saurabh[/QUOTE]
Hi there Saurabh,

there is no RPM in Ubuntu. You are either on the wrong forum or have missed out about the most important feature built into ubuntu/debian: **apt-get**.

Just type from shell **sudo apt-get install yaboot**, that should give you what you are looking for.

/P

---

### Post by sobers_2002 on 2005-09-09
my bad........actually i couldn't find the ypbind tools thru apt and so i was looking to find a binary for it. yaboot as i understand is ppc counterpart (sorta) of grub. what i need is to add this computer to the exiting nis domain. so that it can read user names and passwords from the host and allow logins on the nfs mounted home directories.

thanx
Saurabh

---

### Post by king_arthur on 2005-09-09
[QUOTE=sobers_2002]my bad........actually i couldn't find the ypbind tools thru apt and so i was looking to find a binary for it. yaboot as i understand is ppc counterpart (sorta) of grub. what i need is to add this computer to the exiting nis domain. so that it can read user names and passwords from the host and allow logins on the nfs mounted home directories.

thanx
Saurabh[/QUOTE]

yaboot is a set of binaries which should be included into your install.
I would say it's more similar to LiLo as a concept. Grub is more evoluted.

YaBoot=YetAnotherBoot loader... :D

Once installed with the apt-get command, I suggest you check the man page for yaboot's binaries and relevant sintax with $: man yaboot .

Another source of info of course is the internet online manual: **Google**

:D :D

/P

---


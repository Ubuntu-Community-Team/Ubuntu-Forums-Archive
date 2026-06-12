---
title: "Is it REALLY that hard???"
date: 2006-09-28
forum: Apple PPC Users
---

### Post by [D-Man] on 2006-09-28
I am running a Mac G3 Lombard (Powerbook) with OSX.3.9 and Dapper.  My dual boot worked flawlessly until recently at which time it mysteriously disappeared.  I've read the forum, tried zapping the pram, using option key on start-up, booting from install CD and using rescue mode (which really takes you through the INSTALL process from scratch) and none of these or any other of the many posts I've read seem to have a simple, easy to follow way to RESTORE the yaboot loader or any other solution to restore the dual boot mode without having to re-install ubuntu from start.

Is there anyone that understands how to do this??  Can it be done??  If this problem can't be solved, I (and probably many others) will probably dump ubuntu as this is too much trouble to have to deal with.  

Anyone??

---

### Post by x64Jimbo on 2006-09-28
have a look here: [http://lists.terrasoftsolutions.com/yellowdog-general/March02/0792.html](http://lists.terrasoftsolutions.com/yellowdog-general/March02/0792.html)

---

### Post by [D-Man] on 2006-09-29
> **x64Jimbo said:**
> have a look here: [http://lists.terrasoftsolutions.com/yellowdog-general/March02/0792.html](http://lists.terrasoftsolutions.com/yellowdog-general/March02/0792.html)
x64Jimbo..  thanks man!  That article does not solve the problem but IT DID get me to info that eventually led to my ability to solve the problem and now that I know how to do it... it is EASY!!!

Here's the info I have looked for for countless hours and now offer to others:

1) Boot up into open firmware:  cmd+option+o+f
2) At prompt type:  boot hd:#,\\:tbxi
   (where # = number of your hd partition that has the yaboot)

that is all there is..  but this will NOT fix things permanently but only for the one time you do this.  In order to RESTORE to proper dual boot mode at start up you must use the setenv cmd at the open firmware prompt.  I have not been able to figure that out yet but still experimenting.  Making progress.  If anyone can help..great but I think I will get it in time.

---

### Post by [D-Man] on 2006-09-29
Didn't take as long as I thought!!

at open firmware prompt type:  setenv boot-device hd:#,\\:tbxi
(where # = hard disk partition that has yaboot)

this RESTORES back to normal the dual boot option at start up.

Hope this saves a lot of other people as many hours as I've spent  on this issue.

---


---
title: "Anti virus with incremental update?"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by wadehel on 2006-10-14
Is there any antivirus with incremental update for Ubuntu?

I need regular AV update to keep my neighbours (winXP) live in peace, but I want to do it without eating to much bandwitdh. Is it possible?

---

### Post by Jussi Kukkonen on 2006-10-14
So are you running a mail server for the neighbours, or how does running it improve their mental state? 

To answer the question, take a look at clamav (available in the repos). The update-program was in another package, search for clamav in synaptic or apt-cache to find it.

---

### Post by Haegin on 2006-10-14
If you are on linux the only reason you would need an antivirus program is if you run a mail server or windows machines access files on your pc. Then you would want to scan the email and the files the windows machines access.

---

### Post by wadehel on 2006-10-14
i m not using mail server. I am using stand alone ubuntu, but all of my friends using windows xp, we share file (doc/mp3) oftenly using flashdisk. The flashdisk oftenly goes to cyber cafe (win xp) too.

So i think i need the AV to clean the flashdisk before i plug it to their PC.

---

### Post by Haegin on 2006-10-14
Ok, That makes sense. Take a look at clam av ([http://www.clamav.net/](http://www.clamav.net/)) which is available in the repos. Remember you only want to scan the flash disk not the whole pc (saves time obviously).

---

### Post by wadehel on 2006-10-21
I installed clamav, plus clamTK. But the update still really too big (not incremental?). After few update, wich always make my dialup became unresponsive, i decide to uninstall it.

Thanks :)

---


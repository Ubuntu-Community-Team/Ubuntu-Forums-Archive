---
title: "DPKG and Software Index is Broken."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Shane11 on 2006-09-09
Well it's broken now. (Breezy (still) but wireless now working!).

Tried to install Real Player for video's (RealPlayer 10 works fine for audio).
It 'hung' during installation... I was in a hurry.... 

When I re-booted next day the system advised me that I had a problem.

When using automatic updates: 'Software index is broken'

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Synaptic says 'Unable to get exclusive lock'.

and sudo apt-get install -f 
results in:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I'm a bit stuck now. 

Do I need to do a new install? (not too keen on this because it took me 6 months to get the wireless dongle working!).

Any pointers gratefully received.

Regards
Shane

---

### Post by Shane11 on 2006-09-09
Ah just read cptjaben's post. Should have looked for that first.

Mind you the fix packages hasn't helped me yet.

I'll try a re-boot and see what happens.

Regards to all
Shane.

---


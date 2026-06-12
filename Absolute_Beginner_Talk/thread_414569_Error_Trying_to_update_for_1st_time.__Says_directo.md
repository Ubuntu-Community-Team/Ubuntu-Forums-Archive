---
title: "Error Trying to update for 1st time.  Says directory locked"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by samadams on 2007-04-20
I finally after months of fighting with an Alcatel USB modem, broke down and bought a netopia router/modem.  Now I can get online with Ubuntu!!
However, the system told me I had a bunch of updates to do (about 272 - I'm still using Dapper for now)  and so I clicked on the update icon in the status tray to get started.

I got the list all checked off and clicked the <Install Updates> button.

Here's the error message I got:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Any ideas?

Thanks in advance

---

### Post by lamalex on 2007-04-20
do you have add/remove programs open? or the synaptic repository?

---

### Post by TekMuzik on 2007-04-20
> **samadams said:**
> I finally after months of fighting with an Alcatel USB modem, broke down and bought a netopia router/modem.  Now I can get online with Ubuntu!!
However, the system told me I had a bunch of updates to do (about 272 - I'm still using Dapper for now)  and so I clicked on the update icon in the status tray to get started.

I got the list all checked off and clicked the <Install Updates> button.

Here's the error message I got:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Any ideas?

Thanks in advance

Did you by chance manually add anything to your repository list? I tried to manually add a repo today, and for some reason it gave me that exact same message until I removed the added repository, then it worked fine.

---

### Post by llamakc on 2007-04-20
There's a lockfile in place. Usually folks forget that they have Add/Remove, Synaptic, or some apt-get process running.

---

### Post by samadams on 2007-04-20
neither one is running

---

### Post by samadams on 2007-04-20
I added the Ubuntu CD a while back I'll try and see if that needs to come out, even though I added it through synaptic.  Strange that this would be the reason with an official CD and all.

---

### Post by samadams on 2007-04-20
nope - none of that is running to my knowledge.  However, after some time, the system told me that some updates were complete (I thought it wasn't doing any of them because of the error) and told me I should restart - so I did.  Upon restarting, I clicked the update icon again and all magically works just fine.  hmmmm.....  Anyway - thanks for all the suggestions, must have been just a glitch.

---


---
title: "Can't access Proprietary Drivers Manager"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by razinjap on 2007-10-25
Hi 
I got a problem accessing Proprietary Drivers Manager in 7.10.
When I go System->Administration->Proprietary Drivers Manager for a first time, it asks for a password alright, starts to load the manager and... that's it. Nothing else, like as I didn't click on it at all.
Is there any way to fix it?

---

### Post by mikeyphi on 2007-10-25
> **razinjap said:**
> Hi 
I got a problem accessing Proprietary Drivers Manager in 7.10.
When I go System->Administration->Proprietary Drivers Manager for a first time, it asks for a password alright, starts to load the manager and... that's it. Nothing else, like as I didn't click on it at all.
Is there any way to fix it?

If you have already enabled the repos in Software sources....open Synaptic and try reinstalling 'restricted-manager'

---

### Post by razinjap on 2007-10-26
didn't help...:(

---

### Post by razinjap on 2007-10-27
hey, don't leave me here... help! :confused:

---

### Post by Martje_001 on 2007-10-27
We don't leave you ;). What happens if you do this in a terminal?
```
gksu -D /usr/share/applications/restricted-manager.desktop /usr/bin/restricted-manager
```

---

### Post by razinjap on 2007-10-28
thanks! if i try to call the program from the terminal i get the same result. and... i am sure that both "restricted-manager-core" and "restricted-manager" are installed on my system (at least Synaptic thinks this way).

---


---
title: "[SOLVED] Package Manager in KDE4 - Kubuntu"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by thisismalhotra on 2008-01-14
I don't know if I am the only one having this issue.

I installed KDE 4 on my kubuntu installation. Now when I log into KDE4 and try to use adept, it says my root password in invalid but same works when I log in to KDE 3 session.

Is there a different package manage for KDE4..:confused:
HELP GUYS !!

---

### Post by PmDematagoda on 2008-01-14
The problem you have is something that many people who use an "impure" KDE4 would be having(I have the same problem).

Execute:-
```
sudo adept
```
that should work.

---

### Post by thisismalhotra on 2008-01-14
So, how do I get the pure KDE 4, and is this the same reason I get a lot of crashes in KDE and the screen goes blank white or grey on me??

---

### Post by PmDematagoda on 2008-01-14
You can try out "pure KDE4" by downloading and booting the KDE4 Live CD [here]("http://kubuntu.org/announcements/kde-4.0.php").

---

### Post by pndragon on 2008-01-14
Sorry to interrupt....

Will the the LiveCD work on AMD64?

---

### Post by thisismalhotra on 2008-01-14
Update sudo adept says command not found,

I installed synaptic (which I like by the way) works like charm if I do sudo synaptic, still wont take the password?? Please help as I want adept to work??

---

### Post by PmDematagoda on 2008-01-14
thisismalhotra, I am sorry, the command turned out to be:-
```
sudo adept_manager
```

And pndragon, I am not sure myself, I did not try the Live CD out, there might be an option to get an AMD64 version of it.

---

### Post by leisuresuitgreg on 2008-01-14
> **thisismalhotra said:**
> I don't know if I am the only one having this issue.

I installed KDE 4 on my kubuntu installation. Now when I log into KDE4 and try to use adept, it says my root password in invalid but same works when I log in to KDE 3 session.

Is there a different package manage for KDE4..:confused:
HELP GUYS !!

Hi thisismalhotra

use ```
 sudo passwd 
``` to change your unix password to the root password

Cheers

Greg

---

### Post by thisismalhotra on 2008-01-14
Thanks 

sudo passwd

worked like charm !!

---

### Post by leisuresuitgreg on 2008-01-14
No worries at all!! :)

---


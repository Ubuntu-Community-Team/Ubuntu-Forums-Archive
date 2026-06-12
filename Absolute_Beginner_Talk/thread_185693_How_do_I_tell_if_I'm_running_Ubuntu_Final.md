---
title: "How do I tell if I'm running Ubuntu Final?"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by apt on 2006-06-01
How to I check my version of Ubuntu has been sucessfully updated to Ubuntu 6.0.6 Final. Is there a terminal line I can run to check?

I havent got any updates for the RC version in the last few days.

Adrian

---

### Post by NyTE on 2006-06-01
I think its

[HTML]lsb_release -a[/HTML]

---

### Post by apt on 2006-06-01
This is my output... Its look like I am running the final version, can anyone confim?

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06 LTS
Release:        6.06
Codename:       dapper

---

### Post by bvanaerde on 2006-06-01
Same here.
But somebody who hasn't upgraded in a month or so, should post his output too. This is the only way to be sure, I guess.

I've been doing dist-upgrade on a daily bases, so I guess I already had the final version.

---

### Post by Rackerz on 2006-06-01
I'm guessing you have the final, otherwise it would state that RC was running, although I cannot be sure.

---

### Post by morequarky on 2006-06-01
My output:

LSB Version:    n/a
Distributor ID: Ubuntu
Description:    Ubuntu (The Breezy Badger Release)
Release:        5.10
Codename:       breezy

---

### Post by dvarsam on 2006-06-01
Conclusion:
----------

Launching a Terminal Window & typing:

> lsb_release -a

You get one of the following situations:

1. An "Ubuntu v5.10", prints the following: 

> LSB Version:    n/a
Distributor ID: Ubuntu
Description:    Ubuntu (The Breezy Badger Release)
Release:        5.10
Codename:       breezy

2. An "Ubuntu v6.06 Final", prints the following:

> No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 6.06 LTS
Release: 6.06
Codename: dapper

3. Can anybody running the "RC Release" give us the output of the command "lsb_release -a"?

Thanks.

P.S.> We _ALL_ need to VERIFY whether we are running the "Final" or the "RC" release...

---

### Post by mostwanted on 2006-06-01
If you're running Dapper and there are no new updates to be gained by the update manager, you're running the final. Simple as that.

---

### Post by ubuntu_demon on 2006-06-01
If you are running dapper and have installed all upgrades then you are running Dapper 6.06 LTS final.

---

### Post by macdo on 2006-06-01
I haven't upgraded today, so I'm still on the RC, but the lsb_release -a prints:
```

Distributor ID: Ubuntu
Description:    Ubuntu 6.06 LTS
Release:        6.06
Codename:       dapper

```

---


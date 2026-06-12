---
title: "procinfo: command not found"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by vanthai26 on 2006-11-08
Hi 

I am trying to run procinfo commamd on a ubuntu server but this is what I get 

-bash: procinfo: command not found

Does any one know which apt-get... package I must install in order to use this command?

Thanks

---

### Post by bsussman on 2006-11-08
Just a theory...

procinfo would be my guess

but it is also part of the meta package called utils

---

### Post by mazirian on 2006-11-08
ON a standard debian system, dpkg -S /usr/bin/procinfo says sysutils, but you  probably have that installed already

---

### Post by bsussman on 2006-11-08
> **mazirian said:**
> ON a standard debian system, dpkg -S /usr/bin/procinfo says sysutils, but you  probably have that installed already

Interesting - this is the same meta-pkg as utils on 6.06 - I guess they changed names :)

---

### Post by mazirian on 2006-11-08
Ok, I'm on a ubuntu system now, and the pkg is procinfo afterall.  Sorry to second guess the first and correct answer.  I didn't guess there'd be deviation from debian on something that basic.

---

### Post by bsussman on 2006-11-08
> **mazirian said:**
> Ok, I'm on a ubuntu system now, and the pkg is procinfo afterall.  Sorry to second guess the first and correct answer.  I didn't guess there'd be deviation from debian on something that basic.

And there isn't - procinfo is the recently broken out pkg  and sysutils is the meta package - just like debian AFAIK

---

### Post by vanthai26 on 2006-11-09
It is in the procinfo package after all

sudo apt-get install procinfo

I must have mistype the procinfo when I tried it the first time....

---


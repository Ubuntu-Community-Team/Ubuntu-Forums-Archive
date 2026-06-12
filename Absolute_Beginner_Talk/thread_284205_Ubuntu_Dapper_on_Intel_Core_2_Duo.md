---
title: "Ubuntu Dapper on Intel Core 2 Duo"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by lerio on 2006-10-25
Hi all,

which version of Ubuntu Dapper should I install on my Intel Core 2 Duo Desktop?

x86 or amd64 version? I tried to install both and both are working but I really don't know which one is more suitable for my system and why.

Thanks in advance

---

### Post by Bachstelze on 2006-10-25
If I were you, I'd install the x86 version with a 686 kernel. Do a standard install and when it's complete, install the *linux-686-smp* package.

---

### Post by barkej on 2006-10-25
I would stick to x86 and install a 686 kernel.  The 64bit version works a little faster but software development is in early stages for many programs.  IMHO give the 64bit software another year or so to mature.

---

### Post by lerio on 2006-10-25
wow guys!
you didn't give me even the time to drink a cup of coffee! :) 

i'll certanly follow your advice and i guess that the same logic goes for the upcoming edgy, right?

thanks a lot

---

### Post by Echo35 on 2006-10-25
I attempted a x64 on mine and it didn't work well because of the poor 64-Bit support, so I just stick to the standard version with a 686 like the others said. Works very well. BTW, Core 2 Duo rocks!
 
EDIT: Once that's installed, update manager should update to edgy and keep the 686 just fine.

---

### Post by Bachstelze on 2006-10-25
In edgy ATM there's only a "generic" kernel available and the 686 package is a dummy. I don't know if a 686 optimized kernel will come later.

---

### Post by Echo35 on 2006-10-25
Hmm. Think it'll come out when Edgy is officially released tomorrow?

---


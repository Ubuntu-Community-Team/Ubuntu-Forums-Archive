---
title: "low bogomips"
date: 2006-09-28
forum: Apple PPC Users
---

### Post by rbertran on 2006-09-28
Hi ubuntu users,

I have upgraded my iBook G4 12" to edgy. Also, I have another box, a minimac, with a yellowdog distribution. I have noticed that the applications run slightly faster on the minimac than on my iBook. The processor are more or less the same. Also both, have the same amount of memory. The applications do not have extensive I/O. They are numerical applications or just compilations of large programs. So, why the iBook performs so bad? 

I have checked de bogomips... and I get just only 78 on mi laptop and on the minimac I get 1416... too much diference I guess. Is there any confuguraton tweak that I have forbidden? 

thanks in advance,

Salut!

---

### Post by Brunellus on 2006-09-28
I'm going to move this to the Ubuntu-PPC support groups--they'll have a better idea about that hardware, generally.

---

### Post by APU on 2006-09-28
Since the Hardware of the Mac mini and the iBook is really very similar my guess would be that Yellow Dog optimises more during compilation. The compiler flags used for the kernel could also effect the reported bogomips value - they don´t mean very much anyway.

If you really want to test this out you can always install Gentoo ans optimise like there is no tomorrow ;-)

---


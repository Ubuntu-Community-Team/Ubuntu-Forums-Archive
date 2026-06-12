---
title: "Error after installing packages"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by rjcube on 2006-06-06
Every single time I install a package from Synapic Package Manager in Ubuntu 6.06, it gives me this error:

```
E: emacs21: subprocess post-installation script returned error exit status 1
E: cedet-common: dependency problems - leaving unconfigured
E: eieio: dependency problems - leaving unconfigured
E: speedbar: dependency problems - leaving unconfigured
```

So far programs have worked even after that error, but should I be worried about this at all? and if so how can it be fixed?

I have also tried searching Synaptic for each one of those, installed a few things but they still show up.

---

### Post by morequarky on 2006-06-07
I am NO expert and you need more opinions besides mine.

Do you get the same error when installing a package from a terminal?
Does it happen when you open Synapic, before installing anything?

Have you seen a list of packages that those packages want?
Is it like A needs B which needs C? 

I suspect you need to uninstall those packages and then real quick like reinstall them, which will force it to clear up the dependencies.  But I don't know what those packages DO, so I don't know how harmful that would be.

---

### Post by rcarring on 2006-06-07
Completely remove the four programs you list, and then try installing something small and simple like mc (GNU Midnight Commander) just to check it works.

---


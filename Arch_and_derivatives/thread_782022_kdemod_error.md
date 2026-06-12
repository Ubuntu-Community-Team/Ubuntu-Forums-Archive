---
title: "kdemod error"
date: 2008-05-04
forum: Arch and derivatives
---

### Post by Wicked411 on 2008-05-04
When I try to install kde with kdemod, I enter pacman -S kdemod-complete and then i get error: cannot resolve "libopensync>=0.34

error:failed to prepare transaction  (could not satisfy dependencies) 

kdemod-kdepim-kitchensync requies libopensync

---

### Post by chucky chuckaluck on 2008-05-04
i had a similar problem. this was the solution: **pacman -S kdemod -f kdemod-ui-kdemod**

---

### Post by mips on 2008-05-05
> **Wicked411 said:**
> When I try to install kde with kdemod, I enter pacman -S kdemod-complete ....

Out of curiosity, why are you installing the **complete** kdemod? It kinda defeats the purpose of kdemod and you might as well just install the normal kde if you want everything.

---

### Post by Wicked411 on 2008-05-05
> **mips said:**
> Out of curiosity, why are you installing the **complete** kdemod? It kinda defeats the purpose of kdemod and you might as well just install the normal kde if you want everything.

I heard kdemod is better then just doing that..I dont know something like that.

---


---
title: "MacBook Pro C2D suspend with ATI 7.11"
date: 2007-11-22
forum: Apple Intel Users
---

### Post by acewin on 2007-11-22
Anyone sucessful in getting Suspend to Work on MacBook Pro C2D, using the latest ATI 7.11 driver released yesterday. I have suspend running with custom-configed 2.6.22-9 kernel, but its not stable, suspend does not always resume! The new ATI 7.11, with default gutsy kernel does not fixt it for me.
Any additional pointers might help.
TIA

---

### Post by cyberdork33 on 2007-11-22
> **acewin said:**
> Anyone sucessful in getting Suspend to Work on MacBook Pro C2D, using the latest ATI 7.11 driver released yesterday. I have suspend running with custom-configed 2.6.22-9 kernel, but its not stable, suspend does not always resume! The new ATI 7.11, with default gutsy kernel does not fixt it for me.
Any additional pointers might help.
TIAI didn't even know there was a new version out yet....

The previous drivers didn't account for a change in the linux kernel in how it handles memory, if they still have not fixed that then you will still not get suspend working.

---

### Post by Lagos on 2007-11-25
I had the same problem. Downgraded from Gutsy to Feisty, and now suspend works perfectly.

---

### Post by macaholic on 2007-11-25
I have never gotten suspend to work, which is areal bummer since I always want to use it but end up just shutting down.

---

### Post by cyberdork33 on 2007-11-25
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Attention:_Suspend.2FHibernation_will_not_work](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Attention:_Suspend.2FHibernation_will_not_work)
> **The problem have been supposed to be solved in the AMD Catalyst 7.11 driver release (fully supporting the 2.6.23 and the SLUB allocator kernel).** However this have to be tested... (for me doesn't work yet)

---

### Post by acewin on 2007-11-26
Yup! Does not work for me either.On same notes, anyone got radeonhd driver to work on MBP C2D?
If yes, can you post xorg.conf. TIA

---

### Post by dpope on 2007-12-26
I don't suppose 7.12 improved the situation at all here?

---

### Post by macaholic on 2007-12-27
Well for me, catalyst 7.12, didn't do a thing for suspend. Not sure about anyone else though.

---


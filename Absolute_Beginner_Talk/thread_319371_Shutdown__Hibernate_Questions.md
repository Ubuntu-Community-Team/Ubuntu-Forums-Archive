---
title: "Shutdown / Hibernate Questions"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by j1979c on 2006-12-15
Hello everyone, 
Just installed the edgy eft on my laptop. Really like it. 

Now the question is on the following activities: 
_Shutdown_
When I shutdown edgy eft, it shows me the screen (dunno what's the name for it) where there's a ubuntu logo with a progress bar that decreases. When the progress bar is completely decreased. The screen stays there like forever and the machine is still running.

_Hibernate_
When I choose this option. It just shows something like: 
[ 108.715806] Power down.
And the machine is still running like forever.

So, in both scenarios do I just hit the power switch of my laptop to shutdown the machine? Or is there something wrong?

Thanks, 
Jason

---

### Post by macogw on 2006-12-15
That's not normal.  Mine turns itself off.  If yours is like 10 years old though, it might be normal...

---

### Post by Shatrat on 2006-12-15
I believe this is an acpi related problem.  
You might try booting from grub with the acpi=force option.

---


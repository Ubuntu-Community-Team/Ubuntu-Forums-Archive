---
title: "Uninstalling evolution mail"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-08-29
How do I uninstall it?

would it just be 'sudo apt-get uninstall evolution' ?

---

### Post by Anonii on 2006-08-29
*sudo apt-get remove evolution*

And if you want to remove the configuration too, use:

*sudo apt-get remove --purge evolution*

Good Luck!

---

### Post by Narcoleptic_Insomniac on 2006-08-29
> **Anonii said:**
> *sudo apt-get remove evolution*

And if you want to remove the configuration too, use:

*sudo apt-get remove --purge evolution*

Good Luck!

Worked, thanks.

---

### Post by Toxicity999 on 2006-08-29
might want to skim synaptic for the rest of it's packages. Though, removing some of them cuts out a touch of functionality.

---


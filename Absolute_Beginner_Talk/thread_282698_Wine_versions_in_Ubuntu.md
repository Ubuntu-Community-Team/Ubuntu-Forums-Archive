---
title: "Wine versions in Ubuntu"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by dupa on 2006-10-23
I have a quite simple questions, which versions of Wine is included (by default) in Ubuntu 6.06 and which version will be included in Ubuntu 6.10 ?

Thank you very much!

---

### Post by coffeecat on 2006-10-23
I'm posting from a fully-updated Edgy and the version of wine I installed recently using Synaptic is 0.9.22.0ubuntu3.

I see that you are using 6.06 Dapper. To find out all you have to do is to open Synaptic > search > wine. It tells you the version number that is in the repositories. :wink:

---

### Post by dupa on 2006-10-23
> **coffeecat said:**
> I'm posting from a fully-updated Edgy and the version of wine I installed recently using Synaptic is 0.9.22.0ubuntu3.

I see that you are using 6.06 Dapper. To find out all you have to do is to open Synaptic > search > wine. It tells you the version number that is in the repositories. :wink:

Is 0.9.22.0ubuntu3 included in the default repositories of Ubuntu or you had to manually add the specific repositories of Wine?

Because i prefer to use ONLY the stuff provided directly with ubuntu.
Thank you.

---

### Post by coffeecat on 2006-10-23
As far as I remember, only the main and restricted repositories are enabled by default. I've enabled the Universe and Multiverse repositories in Edgy (and there's a nice new GUI tool called 'Software Sources' under System > Administration for that). But I haven't enabled any third-party (non-Ubuntu) repositories. I can't tell whether wine came from main or universe - Synaptic doesn't tell me that - and I'm not quite sure from your post whether, when you say 'default repositories', you mean main and restricted, or all four Ubuntu repositories.

Suggestion. If you haven't enabled universe, have a look in Synaptic and if wine is listed it must be in main. If not you'll either have to enable universe or, if that's a repository you don't want to use, you'll have to do without wine.

---


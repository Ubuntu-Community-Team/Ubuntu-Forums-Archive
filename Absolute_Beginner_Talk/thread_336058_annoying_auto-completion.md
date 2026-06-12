---
title: "annoying auto-completion"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by pcomelade on 2007-01-11
Hi all,

Auto-completion seems to work odd in my system (Edgy Ubuntu w/KDE). For example, if I write:

$ perl scripts/myscr[tab]
The autocompletion behaves normally and I obtain:
$perl scripts/myscript.pl

But if I type:
$perl -c scripts/mysc[tab]
It can't auto-complete (do nothing)!

It is very annoying since I work basically in Konsole!

Thanks in advance!

M;

---

### Post by jvc26 on 2007-01-11
Is that because you have something else with the perl -c scripts/mysc beginning hence until you put the r in it can't differentiate between the two?
Il

---

### Post by pcomelade on 2007-01-11
No, that's not the case. If I don't type the "-c" option auto-completion performs normally. This is only one example.
I've been working with shells for years and never found this.

Any help?

Thanks,

M;

---

### Post by jvc26 on 2007-01-11
No probs- sorry thought it could be an oversight, sorry my knowledge doesnt run that far with this problem ;) Good luck,
Il

---

### Post by Seine on 2007-01-11
I tried it and note the same behaviour. Interesting really, with perl autocompletion is turned off if there is a flag without a value (even if that flag doesn't take a value).

This is not the case with other executables.  If I type cat -V or python -d auto-completion still works.  Weird. I'd love to know why this is.

---


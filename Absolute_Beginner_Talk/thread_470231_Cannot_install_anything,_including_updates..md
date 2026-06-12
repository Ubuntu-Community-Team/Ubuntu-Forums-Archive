---
title: "Cannot install anything, including updates."
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Jokeaflorias on 2007-06-10
I can't install anything, even the official Ubuntu updates. I'm running Feisty Fawn., Whenever I try to install something, I get this message:
[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

I tried running that command and it said: 
*dpkg: requested operation requires superuser privilege*

Can anybody help me out? 

Thanks,
Jokeaflorias.

---

### Post by brownknight on 2007-06-10
try **'sudo dpkg --configure -a' to correct the problem**. hope this helps.

---

### Post by llamakc on 2007-06-10
Sure, but to be honest you really could have helped yourself on this one. Google would have shown that you need to precede the command with "sudo" and enter YOUR user password.

---

### Post by webmaster5 on 2007-06-10
The Command requires superuser privileges so you must run the Command with the "sudo" command at the beginning.

Like this:
sudo [I]dpkg --configure -a

Hope this Helps!:)
[/I]

---

### Post by Jokeaflorias on 2007-06-10
That worked guys. Thanks a ton, guys. I knew quite a bit about Windows (mostly in the security area), but I still don't understand Ubuntu all that well.

---


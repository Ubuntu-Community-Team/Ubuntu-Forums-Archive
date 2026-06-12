---
title: "weird browser font issue"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by cskid20 on 2007-06-21
The fonts are always bold and italic no matter what I try on the browser's configuration. It is same with different websites also. Terminals and fluxbox's font are fine. I have xubuntu server + xorg + fluxbox + dillo (browser) installed on my computer. I may have messed up something because the problem starts after I remove some packages. Can somebody plz point me to the right direction because I have absolutely no clue what so ever.

---

### Post by deadgobby on 2007-06-21
>the problem starts after I remove some packages
 What packs did you remove? You need to be careful when deleting programs. Like for example if you remove FF. You'll break your system and that is not good. You can try fsck and see if it repairs your system. So open up the terminal and run fsck. Other than that, it is a lesson to be learned.

---

### Post by PaulFr on 2007-06-21
If you have firefox still installed, can you check the same site in Firefox and dillo to see if the problem is only in dillo ?

---

### Post by cskid20 on 2007-06-21
fsck runs after the bootup by default on my comp, and it always said okay... and no I don't have FF installed, so I am not sure if it is a dillo specific issue or not. The problem starts when I installed and then removed synaptic. Is there someway I can fix this font problem cuz its getting annoying.

---

### Post by cskid20 on 2007-06-21
nevermind, I did a fresh install and its back to normal now. Come to think of it, the Xdefault file may has to do with it. Anyways, its done.

---


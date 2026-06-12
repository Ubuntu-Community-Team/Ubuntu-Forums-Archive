---
title: "System Messages?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by glenduncanscott on 2006-10-28
Hey I just upgraded to Edgy (well done, why thankyou!) but where have the boot up messages gone? I know most people don't care whether they see these messages or not, but I found them quite helpful during failures. So is there anyway of enabling these messages again with a simple command?

Thankyou in advance for your suggestions :KS

---

### Post by meng on 2006-10-28
Apparently if you edit your /boot/grub/menu.lst and remove the word 'quiet' from the default boot option, you'll get a verbose boot up.

---

### Post by glenduncanscott on 2006-10-28
Mmmm...ok I commented out the 'quiet' but still no system messages displayed any other suggestions?

---

### Post by meng on 2006-10-28
Sorry to mislead you, it was a suggestion I saw posted elsewhere.

---

### Post by glenduncanscott on 2006-10-28
Thanks anyway, didn't do any harm to try ;-)

---


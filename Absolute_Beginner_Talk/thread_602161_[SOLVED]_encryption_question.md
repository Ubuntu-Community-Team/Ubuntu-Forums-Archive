---
title: "[SOLVED] encryption question"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Phatz on 2007-11-03
I recently installed GnuPG and seahorse.
Upon running it, I was asked to generate a key....followed the prompts, but wasn't really sure exactly what was happening. Anyway, I entered a default password etc and added an "encrypt" script in my Nautilus scripts folder.
 Now, I can encrypt files via right click.
I'm not interested in making files or keys public. I simply want to encrypt local files.
The question is, If I encrypt files and later do a clean install of ubuntu - if I re-install GnuPG and seahorse, will I be locked out of the current encrypted files? Will I have to generate a new key and pass? 
thanks.

---

### Post by haldean on 2007-11-04
If you lose the key you have now, all of your encrypted files will be unopenable. The way you can avoid that is by exporting a copy of your private and public keys (through Seahorse) and saving those somewhere safe - that way you still have them if you have to do a clean install later.

---

### Post by Phatz on 2007-11-04
Thank you very much.

---

### Post by haldean on 2007-11-04
No worries! Please mark this thread as solved (Thread Tools->Mark as Solved) so that other people know that your question has been answered. Thanks!

---


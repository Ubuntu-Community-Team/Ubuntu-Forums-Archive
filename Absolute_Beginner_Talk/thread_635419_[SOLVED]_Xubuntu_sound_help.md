---
title: "[SOLVED] Xubuntu sound help"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by CCNA_student on 2007-12-08
In Ubuntu I can easily change the sound on my laptop. I can press the Fn button and the volume control keys and I can change the volume or I can click on a little volume icon. But in 
Xubuntu my function key does not work(for sound, but the screen brightness does) and I cannot seem to find a way to change the volume. I know this sounds stupid, but could someone please help me.

---

### Post by Orestes on 2007-12-09
Run in a term:

alsamixer

followed by:

alsactl store

to make it permanent. 

HTH

---

### Post by CCNA_student on 2007-12-09
Thanks, that did work.

---

### Post by Orestes on 2007-12-09
Glad to be of service! <Takes a bow>

---


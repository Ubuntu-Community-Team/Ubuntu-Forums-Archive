---
title: "[SOLVED] desktop effects on lenovo r61"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-08-24
hey i'm having some problems with direct rendering on my r61.  it has the Intel GMA X3100 graphics card. i would really like to have beryl back, glxinfo | grep direct gets me this responce

 ricky@ricky-laptop:~$ glxinfo | grep direct
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
ricky@ricky-laptop:~$ 



what can i do?

---

### Post by rickycodie on 2007-08-24
intel wanted me to use mesa instead of opengl. i tried it and it works, but i don't really like it cause it's slow and grainy. 

does anybody know of a way that i can speed the graphics up?

---

### Post by rickycodie on 2007-09-26
bump

---

### Post by rickycodie on 2007-10-28
in gutsy install xgl that's the fix.

---


---
title: "macro"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by utkarshrawat on 2008-02-23
#define KS(p) ks((void *)&p)

Can anyone explain me what this macro is doing

---

### Post by lloyd_b on 2008-02-23
> **utkarshrawat said:**
> #define KS(p) ks((void *)&p)

Can anyone explain me what this macro is doing

It's taking a variable ("p"), and calling a function ("ks()"), passing a void pointer to the variable as a parameter.

It looks like the programmer got tired of typing "ks((void *) &somevar)" and shortened it via the macro to "KS(somevar)".

Lloyd B.

P.S. Questions like this should really be posted in the "Programming" forum, rather than the "Absolute Beginnner" forum...

---

### Post by utkarshrawat on 2008-02-24
Thanks 
Can u explain why do we need Void pointer .I know  we can use a void* any time you need any kind of pointer, without casting
Whats the use of it in  larger project

---


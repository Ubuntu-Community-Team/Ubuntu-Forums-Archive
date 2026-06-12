---
title: "Asterisk"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by dherath10 on 2008-03-17
I installed & configure Asterisks on Ubuntu 7.10 Desktop
But When I configuring asterisk-addons 1.4.6 It gave alot of errors.

chan_ooh323.c:3262: error: ‘struct ooh323_pvt’ has no member named ‘owner’
chan_ooh323.c:3262: error: dereferencing pointer to incomplete type
chan_ooh323.c:3263: error: ‘struct ooh323_pvt’ has no member named ‘owner’
chan_ooh323.c:3263: error: ‘struct ooh323_pvt’ has no member named ‘owner’
chan_ooh323.c:3264: error: ‘struct ooh323_pvt’ has no member named ‘owner’
chan_ooh323.c:3264: error: ‘struct ooh323_pvt’ has no member named ‘owner’
chan_ooh323.c: In function ‘ooh323_convert_hangupcause_asteriskToH323’:
chan_ooh323.c:3284: error: ‘AST_CAUSE_CALL_REJECTED’ undeclared (first use in this function)
chan_ooh323.c:3286: error: ‘AST_CAUSE_UNALLOCATED’ undeclared (first use in this function)
chan_ooh323.c:3288: error: ‘AST_CAUSE_BUSY’ undeclared (first use in this function)
chan_ooh323.c:3290: error: ‘AST_CAUSE_BEARERCAPABILITY_NOTAVAIL’ undeclared (first use in this function)
chan_ooh323.c:3292: error: ‘AST_CAUSE_CONGESTION’ undeclared (first use in this function)
chan_ooh323.c:3294: error: ‘AST_CAUSE_NO_ANSWER’ undeclared (first use in this function)
chan_ooh323.c:3296: error: ‘AST_CAUSE_NORMAL’ undeclared (first use in this function)
chan_ooh323.c:3298: error: ‘AST_CAUSE_FAILURE’ undeclared (first use in this function)
chan_ooh323.c: In function ‘ooh323_convert_hangupcause_h323ToAsterisk’:
chan_ooh323.c:3312: error: ‘AST_CAUSE_CALL_REJECTED’ undeclared (first use in this function)
chan_ooh323.c:3314: error: ‘AST_CAUSE_UNALLOCATED’ undeclared (first use in this function)
chan_ooh323.c:3317: error: ‘AST_CAUSE_BUSY’ undeclared (first use in this function)
chan_ooh323.c:3319: error: ‘AST_CAUSE_BEARERCAPABILITY_NOTAVAIL’ undeclared (first use in this function)
chan_ooh323.c:3322: error: ‘AST_CAUSE_CONGESTION’ undeclared (first use in this function)
chan_ooh323.c:3324: error: ‘AST_CAUSE_NO_ANSWER’ undeclared (first use in this function)
chan_ooh323.c:3328: error: ‘AST_CAUSE_FAILURE’ undeclared (first use in this function)
chan_ooh323.c:3330: error: ‘AST_CAUSE_NORMAL’ undeclared (first use in this function)
chan_ooh323.c: At top level:
chan_ooh323.c:3343: error: expected ‘)’ before string constant
make[1]: *** [chan_ooh323.o] Error 1
make: *** [channels] Error 2

What should I do to overcome the probles

---


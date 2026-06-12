---
title: "KPPP Error. Just error no error code?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by SuperT on 2008-02-12
I am trying to use my Telstra NextG card on ubuntu and finnaly after several days i have discovered kppp, got it to recognise the card and configure it. I have configured it correctly to the best of my knowledge and have done alot of google searching to try and solve this problem with no luck. When i try and connect it gets to the initializing modem stage and then one error appears in the debug window then a few minutes later another error appears and it just keeps goin on. The problem is that it dosnt specify any error code. It just says error? Its not a very god debug tool if it dosnt tell you whats wrong?

Thanks.

---

### Post by dondos on 2008-03-01
As far as I know, kppp is a front-end for wvdial, a command-line utility. You could try to open a terminal window and execute wvdial. This may provide more information than kppp. Also check for a (hidden) text file named .wvdial.conf in your home directory.

---


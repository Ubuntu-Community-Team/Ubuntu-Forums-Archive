---
title: "cd closer question"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by marquee moon on 2007-12-05
when I create a CD using CD/DVD creator, is there a way of not closing the CD so that I can add to it again later?

---

### Post by vikram on 2007-12-05
[B]See 

[/B][http://k3b.plainblack.com/support/k3b-0.12-new-features](http://k3b.plainblack.com/support/k3b-0.12-new-features)
[I][B]
The Automatic Multisession Handling[/B][/I] *When creating multisession CDs in K3b prior to 0.12 you had to always keep in mind to set the multisession mode properly since otherwise K3b would default to close the CD. *
*K3b 0.12 has a new automatic mode which decides which multisession mode to use. K3b does this based on the size of the project, the remaning space on the target CD (or DVD), and of course the data on the target CD. If the project would fill up the CD K3b will close it. Otherwise leave it open to allow other sessions. If the CD already contains a session and has enough space for the project K3b creates a new session and again closes the CD if the new session fills up the CD or leaves it open otherwise. *

---


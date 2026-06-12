---
title: "cardctl ident 'command not found'"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by gyrene2083 on 2007-12-09
Good evening all,

I am having a problem, running the cardctl command.

When I type cardctl ident it says 'command not found'. I searched the forums, and googled before I decided to post, and couldn't come up with a solution. I also tried, the following;
apt-get install pcmcia-cs, and this is what I got back; E: couldn't find package pcmcia-cs.

Any help would be greatly appreciated.

---

### Post by spiderbatdad on 2007-12-09
looks like you havent enabled the repositories. open synaptic. then choose Settings-> Repositories, and select all but sources. then hit the reload button. Then scroll down to the package you're looking for

---

### Post by gyrene2083 on 2007-12-09
spiderbatdad,

Thank you for your help. I went in, and saw that there where tons of repositories. So, I just have to mark them for installation, and I should be good to go. Of course, with the exception of sources. Correct?

---

### Post by spiderbatdad on 2007-12-09
i only suggest enabling them from the synaptic package manager...canonical universe and multiverse should do the trick. then hit the reload arrow and you can scroll down to see the package you want: pcmcia-cs

---

### Post by gyrene2083 on 2007-12-09
Ok, I checked to see if the repositories where enabled and they where. I am still getting the same error msg. Any ideas?

---


---
title: "apt-get  how do i know latest release"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by lupgop on 2008-01-07
an example - i'm reading some instructions on installing denyhosts.
1st i have to install python, as it is written in that language.
so the doc says 
apt-get install python python2.3-dev python2.3

however on checking i'm fairly sure there is a newer version python 3.0a2

how do i know/find out the correct names for this on apt-get 

can i display a list somehow ???? or search or ?


actually looking further the last final release was python 2.5.1 , either way same question.

---

### Post by hyper_ch on 2008-01-07
use this:

```

apt-cache search python

```

This will list all packages that have "python" in the file name or description.

If the list is too long, you can output it to a text file (e.g. on your Desktop):

```

apt-cache search python > ~Desktop/output.txt

```

---


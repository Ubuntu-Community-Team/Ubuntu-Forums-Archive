---
title: "Site Scan + Grab"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by psylance on 2008-04-19
I have this question,

Let's say i have a site serving files, [www.domain.com](www.domain.com).

there are only 5 known sites to public,

[www.domain.com/1](www.domain.com/1)
[www.domain.com/2](www.domain.com/2)
[www.domain.com/3](www.domain.com/3)
[www.domain.com/4](www.domain.com/4)
[www.domain.com/5](www.domain.com/5)

and 5 not known to public,

[www.domain.com/11](www.domain.com/11)
[www.domain.com/21](www.domain.com/21)
[www.domain.com/31](www.domain.com/31)
[www.domain.com/41](www.domain.com/41)
[www.domain.com/51](www.domain.com/51)

Is there any way that people can scan and find out that 11,21,31,41,51 is up running?

---

### Post by quirks on 2008-04-19
"Security" that relies on people not knowing that something exists is very weak. People could just guess URLs and finally find a valid one by coincidence. If you want to be sure, that people cannot access the files, you should implement some sort of access control. I myself don't know how to configure that, but I'm sure there are tons of tutorials on the Internet.

---

### Post by pytheas22 on 2008-04-19
> Is there any way that people can scan and find out that 11,21,31,41,51 is up running?

Definitely...for instance you could write a bash script to use wget or something to automatically go through lots of values and find where content exists or not.  It would a brute-force approach and could take time, but it wouldn't require much intellect.  I would be surprised if there aren't sophisticated tools in existence to do this already.

If your server runs Linux, you can change the permissions on the directories you want to hide so that no one in the public can see them.

---

### Post by psylance on 2008-04-19
Is there any tools or examples to follow? i'm trying to search some .edu sites for studies materials

---

### Post by psylance on 2008-04-20
Anyone can guide me on this/

---

### Post by pytheas22 on 2008-04-25
I found a tool at [http://www.cirt.dk/tools/](http://www.cirt.dk/tools/) that I think can do this--it's the one named WebRoot.pl.  Read the manual, also in the same directory, to figure out how to use it; it takes a little work to get it running, but it will find hidden locations on web servers.

---


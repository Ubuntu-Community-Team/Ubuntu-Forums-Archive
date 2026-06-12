---
title: "location of apache2 program binary file"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by bistro on 2006-09-28
Hi

I thought I found the apache2 program binary file in /usr/sbin/ but the coldfusion installer I'm running says it's not there. I feel a little foolish but I cannot find it - could someone point me in the right direction, please?

Thank you very much.

---

### Post by lamego on 2006-09-28
It is on my Dapper:
> lamego@lamego-desktop:~/_software/debs/g/gq-1.2.0$ which apache2
/usr/sbin/apache2
lamego@lamego-desktop:~/_software/debs/g/gq-1.2.0$


---

### Post by Marsolin on 2006-09-28
Is ColdFusion running as root?  It might not be able to find the binary file in /usr/sbin/ otherwise.

---

### Post by bistro on 2006-09-28
Thank you for the answers - I was mistakenly just specifying the directory, and hadn't typed the filename - it's OK now I've done it properly.

---


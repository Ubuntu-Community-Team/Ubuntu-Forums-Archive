---
title: "How can I access &quot;commercial section of the Ubuntu repository&quot;?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-05-23
Hi,
in article [Ubuntu 6.06 LTS Edition Can Now Download and Deploy IBM DB2 9](http://www.securitysoftwarezone.com/ubuntu-6-06-lts-edition-review441-1.html) in first paragraph there is written DB2 is accessible from the commercial section of the Ubuntu repository. Where is this "commercial section"? How to access this "commercial section"?
Thanks,
Abcuser

---

### Post by Bachstelze on 2007-05-23
Add this in your sources.list :

```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

(replace dapper with edgy or feisty if needed). And remember Google is your friend...

---

### Post by eentonig on 2007-05-23
Open Synaptic and look for the dialogue that allows you to check the other optional repositories.
They're called Universe, Multiverse, ...

---


---
title: "unshadowing the passwd file"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by doober on 2006-06-29
can anyone tell me how to unshadow the passwd file in ubuntu please?

---

### Post by amohanty on 2006-06-29
Why would you want to do that? 
If you havent done so please take a look at as to why you would and would not want it:
[http://www.tldp.org/HOWTO/Shadow-Password-HOWTO-2.html](http://www.tldp.org/HOWTO/Shadow-Password-HOWTO-2.html)

To unshadow it (this is old info - unverified on ubuntu, please verify it on a test boxes before you lock yourself out :)), just replace the **x** after the first colon after every username in **/etc/passwd** with the text between the second and third colon in the **/etc/shadow** file.

Be _very_ _very_ careful about this, know _exactly_ why you are doing this, before you attempt any of this.

HTH
AM

---


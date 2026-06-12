---
title: "Is my box HACKED?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Cabldevil on 2007-12-02
I was going over the auth log and came across this entry, Is it some one logging in or is it just a cron job using su?

Dec  2 09:25:23 server su[5728]: Successful su for clamav by root
Dec  2 09:25:23 server su[5728]: + console root:clamav
Dec  2 09:25:23 server su[5728]: pam_unix(su:session): session opened for user clamav by (uid=0)
Dec  2 09:25:23 server su[5728]: pam_unix(su:session): session closed for user clamav
Dec  2 09:25:00 server gdm[6121]: pam_unix(gdm:session): session opened for user cabldevil by (uid=0)

Thank you in advance.

CD

---

### Post by sethvath on 2007-12-02
Do you have clamav (the antivirus) installed? If so you got your answer. 

If its someone logging in remotely I would like to think they would spend more than a second on your box unleashing whatever payload they have.

---

### Post by Cabldevil on 2007-12-02
yup your correct forgot about that!    

Thanks for the help.

---


---
title: "Problem with root user"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Camellia on 2006-07-26
I have only one account on my computer which comes with the process of ubuntu installaion. And I found that that is not the root user account and doesn't have the permission to modify the /.

Yes I can use the sudo command in shell to do something underneath /, but are there any methods to change my current account to root user account?

BTW: After inputing su command in shell, and also the password afterwards, why it says authorization failed? I'm sure that the password is right. Well, I'm currently using sudo -i instead.

Best regards

---

### Post by catlett on 2006-07-26
```
https://help.ubuntu.com/community/RootSudo
```Using sudo gives you root powers. You can change anything in / not just underneath it.
Here is the official explanation. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by trent dillman on 2006-07-26
also, try gksudo (for gui programs, like synaptic)...

---

### Post by Camellia on 2006-07-27
Thank you guys so much it answers all of my questions:)

---


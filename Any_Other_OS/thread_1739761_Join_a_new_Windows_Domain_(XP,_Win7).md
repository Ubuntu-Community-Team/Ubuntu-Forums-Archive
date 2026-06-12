---
title: "Join a new Windows Domain (XP, Win7)"
date: 2011-04-26
forum: Any Other OS
---

### Post by gunksta on 2011-04-26
The office I work in is, with one exception, a Windows shop. I just installed a new server and am in the process of rolling everyone over to the new domain. The Dell rep told us that in order to join computers to the new network, we would have to demote the computers (XP and Win7) to workgroups and then join them to the new domain. After doing this, we would have to copy files over to the new user.

That seems like a lot of work and I can't find any reference to this on the Internet. I tried just changing the domain name on the computers and they were able to join the new domain, not muss, no fuss. But, I'm wondering if anyone out there can tell me if I'm shooting myself in the foot.

I'm the only Linux user in the office and I'm not worried about my system. I just want to make sure I do the other computers correctly.

Thanks

---

### Post by AztecLogic on 2011-12-05
You do not need to join a workgroup first.  yes, you can join the new domain, the process will automatically dis-join the original domain.

one thing to remembers ever user will create a NEW profile even if the login is exactly the same and you will need to manually move their files from one profile to the new profile.

---

### Post by Dr. C on 2011-12-06
What is the Operating System on the Server?

---

### Post by gunksta on 2011-12-09
The OS is Microsoft Server 2008 R2. In the end, I was able to move the computers directly to the new domain and then copy the user's profile over. Silly process and seemed unnecessarily complex, but it worked out just fine in the end.

I took considerable pleasure in the fact that the Linux system did not require me to copy my files from one profile folder to another. But, in all fairness, authentication on the Windows machines in domain based and my linux laptop just uses the domain to access files and resources.

---


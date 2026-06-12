---
title: "where is service manager in Ubuntu?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-15
Hi
Thank you for reading my post
I tried to remove some service named das which is created by installing a software but i can not find it  using the System>Administration>Services
Is there some other place which allows me to check where this das is created?

as my computer has one DAS (from previous installtion) I can not install the software again.

Thanks

---

### Post by rdd on 2008-01-15
You could try installing bum (actually stands for boot-up-manager). It allows you to control services during startup.

regards 

Tom

---

### Post by carverj on 2008-01-15
Yup, it's called: - 
sysv-rc-conf
Just install it with apt-get/aptitude!

---


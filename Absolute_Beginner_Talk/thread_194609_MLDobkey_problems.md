---
title: "MLDobkey problems"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2006-06-11
Hello there! I've just installed Ubuntu 6.06 server on an old machine here (Duron 800 256mb 15gb hd) and I intend to let it with a CVS + Mldonkey running.
Well, I'm having problems with mldonkey-server. I've got it through apt-get. But it's not working. When I try to telnet the server it refuses, so I tried to run mlnet manually and I get this error:
> vinicius@bedroom:~$ mlnet
No /home/vinicius/.mldonkey/installer.ini found
Resolving [bedroom] ...done
ascii: [ 5(0)(1)(0) d(1)(0)(0) i(3)(0)(0)(2)(0)(4)(0) t o t o(4)(0) t u t u(186)(147) b(16)(196) %  (245)(17)(213)(212) @(224) r(160) X(237) ,(25)(4)(236) ,(25)(4)(18)(0)(0)(0)(12)(0)(0)(0)(0)(7)(0) 1 0 1 0 1 0 0(1)(0)(0)(0)(0)(0)(0)(0)(4)(0) 2 . 2 0(1)(0)(9)(0) 9 9 4 8 9 6 9 8 9(9)(0) 9 9 4 8 9 6 9 8 8(0)(6)(0) t r a t r a(0)(0)(0)(0)(0)(0)(0)(0)(0)(0)]
dec: [(53)(0)(1)(0)(100)(1)(0)(0)(105)(3)(0)(0)(2)(0)(4)(0)(116)(111)(116)(111)(4)(0)(116)(117)(116)(117)(186)(147)(98)(16)(196)(37)(32)(245)(17)(213)(212)(64)(224)(114)(160)(88)(237)(44)(25)(4)(236)(44)(25)(4)(18)(0)(0)(0)(12)(0)(0)(0)(0)(7)(0)(49)(48)(49)(48)(49)(48)(48)(1)(0)(0)(0)(0)(0)(0)(0)(4)(0)(50)(46)(50)(48)(1)(0)(9)(0)(57)(57)(52)(56)(57)(54)(57)(56)(57)(9)(0)(57)(57)(52)(56)(57)(54)(57)(56)(56)(0)(6)(0)(116)(114)(97)(116)(114)(97)(0)(0)(0)(0)(0)(0)(0)(0)(0)(0)]
ascii: [ 5(0)(1)(0) d(1)(0)(0) i(3)(0)(0)(2)(0)(4)(0) t o t o(4)(0) t u t u(186)(147) b(16)(196) %  (245)(17)(213)(212) @(224) r(160) X(237) ,(25)(4)(236) ,(25)(4)(18)(0)(0)(0)(12)(0)(0)(0)(0)(7)(0) 1 0 1 0 1 0 0(1)(0)(0)(0)(0)(0)(0)(0)(4)(0) 2 . 2 0(1)(0)(9)(0) 9 9 4 8 9 6 9 8 9(9)(0) 9 9 4 8 9 6 9 8 8(0)(6)(0) t r a t r a(0)(0)(0)(0)(0)(0)(0)(0)(0)(0)]
dec: [(53)(0)(1)(0)(100)(1)(0)(0)(105)(3)(0)(0)(2)(0)(4)(0)(116)(111)(116)(111)(4)(0)(116)(117)(116)(117)(186)(147)(98)(16)(196)(37)(32)(245)(17)(213)(212)(64)(224)(114)(160)(88)(237)(44)(25)(4)(236)(44)(25)(4)(18)(0)(0)(0)(12)(0)(0)(0)(0)(7)(0)(49)(48)(49)(48)(49)(48)(48)(1)(0)(0)(0)(0)(0)(0)(0)(4)(0)(50)(46)(50)(48)(1)(0)(9)(0)(57)(57)(52)(56)(57)(54)(57)(56)(57)(9)(0)(57)(57)(52)(56)(57)(54)(57)(56)(56)(0)(6)(0)(116)(114)(97)(116)(114)(97)(0)(0)(0)(0)(0)(0)(0)(0)(0)(0)]
s = s2
Fatal error: exception Assert_failure("src/daemon/common/guiEncoding.ml", 1127, 4)


Shouldn't mldonkey create the ini files for me? When I install it using .deb packages it already register it on my init.d directory, so I should not start it manually right?

Any suggestions?

Regards

---

### Post by viniciuscarvalho on 2006-06-11
never mind, it was a time problem, just installed ntpdate and i got it working...

---


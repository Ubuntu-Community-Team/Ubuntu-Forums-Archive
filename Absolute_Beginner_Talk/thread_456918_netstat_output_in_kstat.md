---
title: "netstat output in kstat"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-05-28
i know it is possible to get kstat statistics by giving



> netstat -k



similarily how can we get netstat output using any of the kstat options,



> kstat -*?*


will give the output of netstat.....?

i mean wats the vice versa actually?


i dont know much in detail about netstat/kstat but jus want to know wat will be the 'kstat' command with options to give information on netstat.

---

### Post by sankarv on 2007-05-29
hi i got it,

it is


kstat -c net


will list the n/w related parameters.

---


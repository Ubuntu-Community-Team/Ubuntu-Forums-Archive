---
title: "Help With Wget Output We are Newbiez"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by delegate on 2007-06-28
We are downloading files using wget. At the end we want to calculate throughput for each file. So below is the output given by wget.
[ftp://xxx.xxx.xxx.xxx/15MB--20:56:52](ftp://xxx.xxx.xxx.xxx/15MB--20:56:52)
Connecting to xxx.xxx.xxx.xxx:xx... connected.
Logging in as xxxxx ... Logged in!
==> SYST ... done. ==> PWD ... done.
==> TYPE I ... done. ==> CWD not needed.
==> PASV ... done. ==> RETR 15MB ... done.
Length: 15,769,600 (15M)

100%[======================================>] 15,769,600 10.91M/s

20:56:53 (10.90 MB/s)- `15MB' saved [15769600]

real 0m1.486s
user 0m0.044s
sys 0m0.188s


what is 10.90 MB/s----what can we call it----can we call it throughput---what term best describes 10.90 MB/s---when we calculate throughput say eg 15 MB(file size)/time(0m1.486s) we are getting a figure different from 10.90MB/s

So what can we call 10.90MB/s---coz we want also to graph it.

If 10.90 MB/s is throughput how can we separate it from---throughput we are calculating using the formula(15 MB(file size)/time(0m1.486s) )

Your help is greatly appreciated we are newbies

---

### Post by delegate on 2007-06-28
> **delegate said:**
> We are downloading files using wget. At the end we want to calculate throughput for each file. So below is the output given by wget.
[ftp://xxx.xxx.xxx.xxx/15MB--20:56:52](ftp://xxx.xxx.xxx.xxx/15MB--20:56:52)
Connecting to xxx.xxx.xxx.xxx:xx... connected.
Logging in as xxxxx ... Logged in!
==> SYST ... done. ==> PWD ... done.
==> TYPE I ... done. ==> CWD not needed.
==> PASV ... done. ==> RETR 15MB ... done.
Length: 15,769,600 (15M)

100%[======================================>] 15,769,600 10.91M/s

20:56:53 (10.90 MB/s)- `15MB' saved [15769600]

real 0m1.486s
user 0m0.044s
sys 0m0.188s


what is 10.90 MB/s----what can we call it----can we call it throughput---what term best describes 10.90 MB/s---when we calculate throughput say eg 15 MB(file size)/time(0m1.486s) we are getting a figure different from 10.90MB/s

So what can we call 10.90MB/s---coz we want also to graph it.

If 10.90 MB/s is throughput how can we separate it from---throughput we are calculating using the formula(15 MB(file size)/time(0m1.486s) )

Your help is greatly appreciated we are newbies

i think its u can call it instant throughput

---

### Post by delegate on 2007-06-28
> **delegate said:**
> We are downloading files using wget. At the end we want to calculate throughput for each file. So below is the output given by wget.
[ftp://xxx.xxx.xxx.xxx/15MB--20:56:52](ftp://xxx.xxx.xxx.xxx/15MB--20:56:52)
Connecting to xxx.xxx.xxx.xxx:xx... connected.
Logging in as xxxxx ... Logged in!
==> SYST ... done. ==> PWD ... done.
==> TYPE I ... done. ==> CWD not needed.
==> PASV ... done. ==> RETR 15MB ... done.
Length: 15,769,600 (15M)

100%[======================================>] 15,769,600 10.91M/s

20:56:53 (10.90 MB/s)- `15MB' saved [15769600]

real 0m1.486s
user 0m0.044s
sys 0m0.188s


what is 10.90 MB/s----what can we call it----can we call it throughput---what term best describes 10.90 MB/s---when we calculate throughput say eg 15 MB(file size)/time(0m1.486s) we are getting a figure different from 10.90MB/s

So what can we call 10.90MB/s---coz we want also to graph it.

If 10.90 MB/s is throughput how can we separate it from---throughput we are calculating using the formula(15 MB(file size)/time(0m1.486s) )

Your help is greatly appreciated we are newbies

i think  u can call it instant throughput

---


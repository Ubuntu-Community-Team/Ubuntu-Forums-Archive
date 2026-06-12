---
title: "Installing rp-pppoe-3.8"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Felcon on 2007-05-20
Hi...

         I've just installed ubuntu 7.04 and now trying to get my internet connection up and running. I'm using an conexant AccessRunner USB ADSL modem and when I boot up Ubuntu the red light start blinking and stay on..So I knw that my modem is working. Now I'm trying to install an Internet client to connect to the internet but when I try to install rp-pppoe-3.8 I get this message

> lloyd@Felcon:~/rp-pppoe-3.8$ ./go
Running ./configure...
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
Oops!  It looks like ./configure failed.

    According to the Readme which comes with rp-pppoe-3.8 , I need to have pppd preinstalled. I googled it but couldn't find that package..How could I install it. 

       I'm really interested in using ubuntu and learn it..But without internet I can't do anything..So can you please help me with this problem.. Since I'm a newbie I appreciate if you can give me step-by-step instructions..tnkz..

---

### Post by arthurD on 2007-06-19
there is actually a pppoe package for ubuntu
[http://packages.ubuntu.com/hoary/net/pppoe]("http://packages.ubuntu.com/hoary/net/pppoe")

So installing via package manager or apt/aptitude should work fine.
At least it worked for me on dapper

---


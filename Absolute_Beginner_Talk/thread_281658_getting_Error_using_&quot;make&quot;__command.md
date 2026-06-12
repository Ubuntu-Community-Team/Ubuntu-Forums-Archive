---
title: "getting Error using &quot;make&quot;  command"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by kodachrome64 on 2006-10-21
I'm trying to compile cowpatty 2.0 using make command and I get this error.
Can anyone point me in the right direction?


-----
adam@ubuntu-macbook:~/Desktop$ cd cowpatty
adam@ubuntu-macbook:~/Desktop/cowpatty$ ls
AUTHORS    COPYING     CVS            FAQ       md5.c   sha1.c  utils.c
CHANGELOG  cowpatty.c  dict           INSTALL   md5.h   sha1.h  utils.h
common.h   cowpatty.h  eap-test.dump  Makefile  README  TODO    WISHLIST
adam@ubuntu-macbook:~/Desktop/cowpatty$ sudo make
Password:
cc -pipe -Wall -DOPENSSL -O3   -c -o md5.o md5.c
cc -pipe -Wall -DOPENSSL -O3   -c -o sha1.o sha1.c
sha1.c: In function ‘pbkdf2_sha1_f’:
sha1.c:151: warning: pointer targets in initialization differ in signedness
sha1.c:167: warning: pointer targets in passing argument 1 of ‘hmac_sha1_vector’  differ in signedness
sha1.c:172: warning: pointer targets in passing argument 1 of ‘hmac_sha1’ differ  in signedness
sha1.c: In function ‘sha1_prf’:
sha1.c:219: warning: pointer targets in initialization differ in signedness
sha1.c:219: warning: pointer targets in initialization differ in signedness
sha1.c:219: warning: pointer targets in initialization differ in signedness
cc -pipe -Wall -DOPENSSL -O3   -c -o utils.o utils.c
cc -pipe -Wall -DOPENSSL -O3   -c -o cowpatty.o cowpatty.c
cowpatty.c: In function ‘getpacket’:
cowpatty.c:270: warning: implicit declaration of function ‘pcap_next_ex’
cc -pipe -Wall -DOPENSSL -O3 cowpatty.c -o cowpatty utils.o md5.o sha1.o -lpcap -lcrypto
cowpatty.c: In function ‘getpacket’:
cowpatty.c:270: warning: implicit declaration of function ‘pcap_next_ex’
/tmp/ccU7btyW.o: In function `getpacket':cowpatty.c:(.text+0x2ef): undefined ref erence to `pcap_next_ex'
/tmp/ccU7btyW.o: In function `main':cowpatty.c:(.text+0xacf): undefined referenc e to `pcap_next_ex'
:cowpatty.c:(.text+0xd60): undefined reference to `pcap_next_ex'
collect2: ld returned 1 exit status
make: *** [cowpatty] Error 1
adam@ubuntu-macbook:~/Desktop/cowpatty$
adam@ubuntu-macbook:~/Desktop/cowpatty$

---

### Post by jordanmthomas on 2006-10-21
```
/tmp/ccU7btyW.o: In function `getpacket':cowpatty.c.text+0x2ef): undefined ref erence to `pcap_next_ex'
/tmp/ccU7btyW.o: In function `main':cowpatty.c.text+0xacf): undefined referenc e to `pcap_next_ex'
```

I'm not sure, but it looks like the program isn't coded correctly.  Maybe you could ask the people who make cowpatty?

---

### Post by lreyes6 on 2006-10-21
did you run a ```
./configure
``` for me is a dependency problem

---

### Post by jordanmthomas on 2006-10-21
Oooh, didn't see that.  He didn't configure.

---

### Post by lreyes6 on 2006-10-21
but some programs doen't bring a configure  script... but in those cases the INSTALL or the README tells what do you need :D:D

---

### Post by jordanmthomas on 2006-10-21
Oh, and actually, there was no conifgure script according to his post

---

### Post by lreyes6 on 2006-10-21
yeap i just saw that jejejeje :mrgreen:

---

### Post by kodachrome64 on 2006-10-21
Leonel,

Thanks for your advise. How and where/ when should I use the 

./configure

command?

Is it as simple as entering "./configure" in the terminal before using "make"
comand in terminal?

---

### Post by jordanmthomas on 2006-10-21
I know I am not Leonel, but I am going to help anyway.

You should only use ./configure if there is in fact a file called configure in your directory.  When you typed ls and didn't see a configure, you know you don't need to run it.  Make sense?  

Your best bet is to always read the README and INSTALL files that are usually there.  Not configuring wasn't your problem here, though.

---

### Post by hod139 on 2006-10-21
You shouldn't be using sudo.  You should just enter the command make.  Also, read the INSTALL file for specific instructions.  For installing, you "may" need sudo rights, but not for building.

**EDIT:** Also, make sure you have the package libpcap-dev installed.

---

### Post by kodachrome64 on 2006-10-22
Thanks all for advise and suggestions. I found the problem was that I had a folder with spaces in the make path. Folder name was "apps installs" I changed it to "apps_installs" and all worked.

---

### Post by slugvision on 2008-02-10
hmm this app does not contain a configure file...... and ive installed all the things mentioned above. this is a good network tool too

---

### Post by dalphim on 2008-04-26
install libssl-dev
install libpcap0.8-dev

and make again

---


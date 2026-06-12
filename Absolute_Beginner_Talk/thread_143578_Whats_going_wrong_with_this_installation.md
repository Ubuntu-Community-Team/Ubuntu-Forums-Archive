---
title: "Whats going wrong with this installation?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by TheBigGeeUK on 2006-03-12
I've been following this to the letter to install my USB adapter: 

[https://wiki.ubuntu.com/WifiDocs/Driver/zydas_zd1211?highlight=%28safecom%29](https://wiki.ubuntu.com/WifiDocs/Driver/zydas_zd1211?highlight=%28safecom%29)

but I get this in response when I go to

```
make clean && make && make install
```

```
ncomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9118: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c: At top level:
/home/gee/zd1211-driver-r52/src/zd1205.c:9137: error: syntax error before ‘plcp_wla_Header_t’
/home/gee/zd1211-driver-r52/src/zd1205.c:9138: warning: function declaration isn’t a prototype
/home/gee/zd1211-driver-r52/src/zd1205.c: In function ‘zd1205_CheckOverlapBss’:
/home/gee/zd1211-driver-r52/src/zd1205.c:9139: error: ‘u8’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9139: error: ‘pByte’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9140: error: syntax error before ‘currPos’
/home/gee/zd1211-driver-r52/src/zd1205.c:9147: error: ‘pMacBody’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9148: error: ‘currPos’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9150: error: ‘bodyLen’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9152: error: ‘elemId’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9153: error: ‘elemLen’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9157: error: ‘gAP’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9158: error: ‘ErpInfo’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c: In function ‘zd1205_HandleQosRequest’:/home/gee/zd1211-driver-r52/src/zd1205.c:9183: error: ‘sw_tcb’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9185: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9186: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9188: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c: In function ‘zd1205_notify_join_event’:
/home/gee/zd1211-driver-r52/src/zd1205.c:9204: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9216: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9218: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9221: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9223: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c: In function ‘zd1205_notify_disjoin_event’:
/home/gee/zd1211-driver-r52/src/zd1205.c:9234: error: ‘KERN_DEBUG’ undeclared (first use in this function)
/home/gee/zd1211-driver-r52/src/zd1205.c:9234: error: syntax error before string constant
/home/gee/zd1211-driver-r52/src/zd1205.c:9244: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9247: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c: In function ‘zd1205_notify_scan_done’:/home/gee/zd1211-driver-r52/src/zd1205.c:9260: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c: In function ‘hostap_michael_mic_failure’:
/home/gee/zd1211-driver-r52/src/zd1205.c:9294: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9295: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9295: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9295: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9295: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9295: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9295: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9299: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9300: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9300: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9300: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9300: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9300: error: dereferencing pointer to incomplete type
/home/gee/zd1211-driver-r52/src/zd1205.c:9300: error: dereferencing pointer to incomplete type
make[2]: *** [/home/gee/zd1211-driver-r52/src/zd1205.o] Error 1
make[1]: *** [_module_/home/gee/zd1211-driver-r52] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [all] Error 2
root@Family-Ubuntu:~/zd1211-driver-r52#

```

Anyone have a clue cos I certainly don't!

Gee

---

### Post by Dullin on 2006-03-13
Have you tried from both download locations that the HowTo gives you?

They seem to say that for some unexplainable reason it doesn't always work with the first download.

---

### Post by TheBigGeeUK on 2006-03-13
I've just tried the other installation and get the same error. I'm finding that I'm having a lot of problems installing anything to be honest, even when I'm following other peoples walkthroughs. I get the same error for all of them.

I get the same error trying to install opera.

I've tried installing aMSN (using automatix) which works, but I get my synaptic package manager saying theres a broken link and to remove it!

When trying to install other apps, when I use the ./configure I get 

```
bash: configure: command not found

```

Once you install Ubuntu 5.10 Breezy badger, is there something I need to do it, like update any bugs or anything? If so how?

In the synaptic package manager, in repositories, what should be in there?

Gee

---

### Post by TheBigGeeUK on 2006-03-13
Oh another thing Gaim Instant messenger won't connect (the reason why I tried aMSN).

Also evolution mail, more often than not won't get my mail, just time's out saying it was unable to connect to POP or IMAP servers (I've tried both), but yet it has connected on some occasions???

I must emphasise that I can connect to my router using a wired connection, but don't wish this to remain!

Gee

---


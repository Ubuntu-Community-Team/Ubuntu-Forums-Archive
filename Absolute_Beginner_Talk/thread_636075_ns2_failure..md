---
title: "ns2 failure."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by thorosius on 2007-12-09
I am using ns2.28 allinone on my Edgy. Other ns components are installing easily. When the install script installs ns-2.28 there is an error.
```
 
[FONT=Courier New][FONT=Tahoma][SIZE=2][COLOR=dimgray]./sctp/sctp.h:630: error: extra qualification ‘SctpAgent::’ on member ‘DumpSendBuffer’[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Courier New][COLOR=dimgray]make: *** [trace/trace.o] Error 1[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=dimgray]Ns make failed![/COLOR][/FONT][/SIZE]
[/FONT]

```
 
Can anyone help me with this?

---

### Post by nikoPSK on 2007-12-09
did you configure it?
```
./configure
```
or
```
./autogen.sh
```

---


---
title: "rp-pppoe USB amedyn connection"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by BKK on 2006-05-13
Hello.

I have been wrestling getting my adsl going. I have followed numerous how-to's!

when I run amstart.sh everything goes flawlessly right to the very last line before it should say "connected" 
 ie.
>>>>>Activating Interface
>>>>>Loading pppd daemon 

then it gives me this error

The file /etc/ppp/peers/dsl-provider does not exist. Please create it or use a command line argument to use another file.

I am just not sure what file it is looking for? What should this file have in it. I can simply create one in a text editor and rename it to dsl-provider.

I just need to know what exactly to type into this file!

Thanks!

edit: is it looking for chap-secrets or pap-secrets???

edit: I ran pppoeconf after this finished, rebooted n ran amstart.sh again, this time it passed that point now, I get it telling me that /usr/lib/pppd/2.4.3/rp-pppoe.so doesnt exist>!>! I KNOW its there! I went there and checked! It say it doesnt exists an can not open! WTF??

I got this far before and didnt know what to do! should I just get an ethernet connected modem and reinstall ubuntu and be done with this mess??

---

### Post by BKK on 2006-05-13
what can I do?^^^

---


---
title: "Nokia N80 -- GPRS"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by nwo on 2006-07-24
I can't configure pppd for my Nokia N80 phone. I've tried to use my old connection script (my phone is seen in /proc/net/irda/discovery), but it doesn't work:

```

$ cat /etc/ppp/peers/gprs
/dev/ircomm0 57600
lock
modem
ipcp-accept-local
ipcp-accept-remote
usepeerdns
defaultroute
noipx
novj
novjccomp
noipdefault
user user_name
password my_password
defaultroute
connect '/usr/sbin/chat -v -E -f /etc/ppp/scripts/gprs'

$ cat /etc/ppp/scripts/gprs 
ABORT "NO CARRIER"
ABORT "NO DIALTONE"
ABORT "NO ANSWER"
ABORT "ERROR"
ABORT "BUSY"
"" "at"
OK "at+CGDCONT=1,\042IP\042,\042internet.some_domain.com\042,\0420.0.0.0\042,1,1"

OK "atd*99#"
CONNECT

```

When I try to establish connection via usb cable, the problem is the same. These configs were okay for my previous Nokia phone. Please help! ](*,)

---


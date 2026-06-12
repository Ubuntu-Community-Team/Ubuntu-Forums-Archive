---
title: "Wvdial Error"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by LivingSouL on 2006-10-28
Anyone can help me on xubuntu edgy? my dialer disconnects and it says authentication error but i did check the uname and pwd many times. maybe some config i dont know. pls help.

```
root@xubuntu:/etc# wvdial
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT101355
--> Waiting for carrier.
ATDT101355
CONNECT 57600 
--> Carrier detected.  Waiting for prompt.
************************************************
*  Product Name    :Quidway A8010;             *
*  Product Provider:HuaWei;                    *
*  Internet Server :######;                    *
************************************************
        Welcome to INTERNET!
    Please input username:
    Please input password:
--> Looks like a password prompt.
--> Sending: (password)
**********
    VPN user,Please continue...
~[7f]}#@!}!"} }=}!}$}%\}"}&[7f][7f][7f][7f]}%}&[1c]}6}&\}1}$}%\}2}"}3}#}!}=O~
--> PPP negotiation detected.
--> Starting pppd at Sat Oct 28 14:09:01 2006
--> Pid of pppd: 5483
--> Using interface ppp0
--> pppd: &#65533;Y
--> [06][08]([0c][06][08]
--> pppd: &#65533;Y
--> [06][08]([0c][06][08]
--> pppd: &#65533;Y
--> [06][08]([0c][06][08]
--> pppd: &#65533;Y
--> [06][08]([0c][06][08]
--> pppd: &#65533;Y
--> [06][08]([0c][06][08]
--> Disconnecting at Sat Oct 28 14:09:07 2006
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

```

---


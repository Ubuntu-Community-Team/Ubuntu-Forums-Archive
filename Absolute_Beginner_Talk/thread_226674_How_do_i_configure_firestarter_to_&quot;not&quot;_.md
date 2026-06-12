---
title: "How do i configure firestarter to &quot;not&quot; reply to a ping..??"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-07-31
I pass everything but the ping requests...



> ----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2006-07-31 at 18:12:39

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: FAILED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

----------------------------------------------------------------------





And why can't i set it to **PPP** dial-up modem..??? , The only options are ethernet device and ipv6 tunnel....And now i can't turn the firewall back on...

---

### Post by jason.b.c on 2006-07-31
> And now i can't turn the firewall back on...

All right , I got it turned back on now ...

And it see's my external serial modem again....


PING....???? :confused: #-o

---

### Post by jason.b.c on 2006-07-31
So does the [COLOR="Blue"]blue[/COLOR] icon turn [COLOR="Red"]red[/COLOR] when i'm being pinged..???

'cause it keeps happening...:confused:

---

### Post by 5-HT on 2006-07-31
There are ICMP filtering options available in the preference settings.

---

### Post by jason.b.c on 2006-07-31
> **5-HT said:**
> There are ICMP filtering options available in the preference settings.

Yea i saw that but it still replies to a ping.!

Are the options supposed to be **checked or unchecked**..???  Because i tried it both way's......

---

### Post by jason.b.c on 2006-07-31
Anyone know...????        :confused:

---

### Post by T700 on 2006-07-31
Not sure with Firestarter, but you can download the Guard Dog configuration program and one of the settings is not to reply to a ping.

Paul

---

### Post by jason.b.c on 2006-07-31
> **T700 said:**
> Not sure with Firestarter, but you can download the Guard Dog configuration program and one of the settings is not to reply to a ping.

Paul

So does firestarter , But it still replies either way around... =; 

Thats what i can't figure out...#-o 

I was completely stealthed in windows....Thats awesome..

---

### Post by 5-HT on 2006-08-01
> **jason.b.c said:**
> Yea i saw that but it still replies to a ping.!

Are the options supposed to be **checked or unchecked**..???  Because i tried it both way's......

When 'Enable ICMP filtering' is checked, all the uncheked packet types should be denied. To allow any given packet type ICMP filtering will need to be enabled and the packet type checked.

HTH

---

### Post by jason.b.c on 2006-08-01
> **5-HT said:**
> When 'Enable ICMP filtering' is checked, all the uncheked packet types should be denied. To allow any given packet type ICMP filtering will need to be enabled and the packet type checked.

HTH

I passed..!!    YEA...:D 

> ----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2006-08-01 at 11:02:46

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

----------------------------------------------------------------------



Cool...O:)

---


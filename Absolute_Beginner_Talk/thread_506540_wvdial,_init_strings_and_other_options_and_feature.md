---
title: "wvdial, init strings and other options and features!"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-07-21
So I'm wanting to understand my wvdial configuration better, and to learn about what other things I can do.

Here is my wvdial configuration.
```

[Dialer Defaults]
Modem Type = Analog Modem
Dial Command = ATDT
Baud = 115200
ISDN = 0
Carrier Check = no
Stupid Mode = yes
FlowControl = CRTSCTS
Modem = /dev/ttyS0
Phone = 086767000
Username = guysmiley25
Password = xxxxxx
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = ATM0
Init4 = ATX3

```

It's really the Init strings that I'm wondering about.

I understand that ATX3 tell the modem to redial if the connection is dropped. And ATM0 tell the modem to shut up. I do not know what the rest means. And what other options are.

Is there away I can tell the modem to pickup the line, if there is a dial tone, then dial. If no dial tone then wait x seconds then try again. Also if connected and a call comes though (call waiting), drop the connection. Also maybe make it so if the 5 key is pressed on a hand set, then drop the connection and try again in x seconds.

So the effect is that using the phone line for phone calls is a priority over the internet. If someone rings they will get though, and if the internet is connected and you want to dial out, you just press 5.

That would be cool. But just any information on anything that I could do would be awesome. Also I would like to know about syntax of init strings.

Thanks.

---

### Post by Bartender on 2007-07-22
I just googled it
[http://www.modemhelp.org/inits/index.html](http://www.modemhelp.org/inits/index.html)
[http://www.modemsite.com/56k/trouble2.asp](http://www.modemsite.com/56k/trouble2.asp)
[http://www.modemhelp.net/basicatcommand.shtml](http://www.modemhelp.net/basicatcommand.shtml)

Not saying I understand any of this, but there's lots more where that came from :)

---


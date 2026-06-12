---
title: "handshaking"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by aritrakundu on 2008-03-31
dear friends,
i have having problems of communicating between two terminals using rs232. I am using an usb-serial adapter. So in the /dev the 2 ports showed up as ttyUSB0 and ttyUSB1. Now I used this commands to set up the ports. In the firat terminal i typed
stty 9600 cs8 -istrip -parenb < /dev/ttyUSB0 and
stty 9600 cs8 -istrip -parenb < /dev/ttyUSB1

then opening up another terminal i typed 
cat /dev/ttyUSB0

and then again in the first terminal i typed 
echo ".........something" > /dev/tty/USB1

but i can get nothing.    How to configure then??

thank you in advance
Aritra

---

### Post by Diabolis on 2008-04-01
I have used minicom to communicate with a serial port to a cisco router using a usb adapter, so give it a try.

[http://www.cpqlinux.com/serialconsole.html](http://www.cpqlinux.com/serialconsole.html)

[http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html](http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html)

You can google for minicom and find lots of tutorials and step by step guides. Hope it helps.

Also remember to use the same settings for **both** ports.

Probably you want to start with this:
```
minicom -s
serial port setup

```

---


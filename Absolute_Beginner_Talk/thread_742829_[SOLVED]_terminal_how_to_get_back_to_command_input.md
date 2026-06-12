---
title: "[SOLVED] terminal how to get back to command input line?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by tettayes on 2008-04-02
I know I sound very silly, but when I do ping in terminal, it just keep going until I close the terminal window.
Could anyone teach me how to stop ping-ing??
I think I used to know, but somehow, forgot!

Thank you very much!

---

### Post by hyper_ch on 2008-04-02
ctrl-c

---

### Post by amaroKer on 2008-04-02
Most commands have a --help operator to assist you.

Here is the result from ping --help
```
logan@logan-desktop:~$ ping --help
ping: invalid option -- -
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
logan@logan-desktop:~$ 

```

It looks like you need to run ```
ping XXX.XXX.XXX.XXX -c 5
``` to get 5 pings only.

---

### Post by tettayes on 2008-04-02
thanks for a quick reply!
it worked...ehh, another lesson for today!

thanks again

---


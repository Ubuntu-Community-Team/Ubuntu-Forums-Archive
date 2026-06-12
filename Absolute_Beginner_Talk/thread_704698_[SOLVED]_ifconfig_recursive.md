---
title: "[SOLVED] ifconfig recursive?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by coloclone on 2008-02-22
Hi All!

How do I enter a command such as ifconfig and pipe to whatever so that I can view it in the term and have it update realish time?

My synaptic GUI went to non-interactive mode and I want to monitor the transfer... Or does anyone know how to get out of non-interactive mode? 

Thanks!!

Cliff

---

### Post by Cypher on 2008-02-22
```

while 1; do ifconfig <interface>; sleep 5; done

```
Where <interface> could be ETH0, ETH1, WLAN0 or something..

Hit CTRL-C when you want to stop..

---

### Post by coloclone on 2008-02-22
In BASH or SH I'm getting a '1 not found'? Ideas?

Edit: Oh forgot to say thanks!

---

### Post by Cypher on 2008-02-22
oh..my bad..let's try..
```

while [ 1 ]; do ifconfig <interface>; sleep 5; done

```
That's what happens when I don't pay attention..:-D

---

### Post by coloclone on 2008-02-22
Bwaha! That was it!

[Virtual High-5]

Thanks again!!!

:guitar:

---


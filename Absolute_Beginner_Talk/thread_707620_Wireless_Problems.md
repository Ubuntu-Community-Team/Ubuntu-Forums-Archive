---
title: "Wireless Problems"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Nifter on 2008-02-25
I have a time laptop and a ten digit hex code for wireless internet but it doesnt seem to work...

The wireless connector finds the network but then it asks for whether it is "open access" or "shared key" and neither seem to work

any ideas?

Nifter

---

### Post by northern lights on 2008-02-25
How is your wireless encrypted - WEP, WPA, WPA2?

Have you possibly not set the same in Ubuntu?

What wireless card is in your comp?

---

### Post by Nifter on 2008-02-25
WEP encrypted
3com card
goes with "WEP 64/128 bit Hex"

---

### Post by jan quark on 2008-02-25
please post the output of the following terminal commands

```
iwconfig
```
```

cat /etc/network/interfaces
```

---

### Post by Nifter on 2008-02-25
what?
i do not understand code

---

### Post by northern lights on 2008-02-25
In the top panel, navigate  to "Applications > Accessories > Terminal".

Now in the newly opned window, type the above commands. It will look something like```
user@host:~$
```
Now type:```
user@host:~$ cat /etc/network/interfaces
```
Hit Enter. Copy everything from the first pound (#) to the new prompt (user@...) and paste it here.

Do the same with ```
user@host:~$ iwconfig
```

---

### Post by jan quark on 2008-02-25
sry for giving not enough info :(

but after a while you get used to it too :)

---

### Post by Sordelka on 2008-02-25
If he has a clean installation of Ubuntu, means that he did not install ndiswrapper! Nearly all wireless cards require it to work.

Several installation guides are available in here, just search for Ndiswrapper.

---


---
title: "25 Character WEP Key Not Accepting"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by kolisikepu on 2008-04-09
Hi Community,

Disperately needing help with this WEP key.

I have posted something before about this issue, but not many replied. I tried going somewhere else to find some help, but that was no good either.

The Issue.... and please don't give me lectures about WEP is not secure and what not... I already know that, but this is something work has configured everywhere on our wireless.

...back to the issue...
Our work wireless is configured for 128bit WEP. My windows can connect to it with no issues. My Linux though (even Apple has the same problem) won't accept 25 characters for 128bit ascii WEP key. It'll only go as far as 13 characters and that's it.

Any suggestions as to how I can over right this without changing settings on the wireless router?

---

### Post by fastTalker on 2008-04-09
i assume you are using Network Manager or the like to connect.  have you tried doing it from the command line?

```

$ iwconfig wlan0 essid *networkname*
$ iwconfig wlan0 key *######*...

```

also, i think the key should probably be 26 characters.

if you have it in the form of a password (not passphrase) rather than the hex key. append it with ***s:***.

---

### Post by kolisikepu on 2008-04-09
> **fastTalker said:**
> i assume you are using Network Manager or the like to connect.  have you tried doing it from the command line?

```

$ iwconfig wlan0 essid *networkname*
$ iwconfig wlan0 key *######*...

```also, i think the key should probably be 26 characters.

if you have it in the form of a password (not passphrase) rather than the hex key. append it with ***s:***.

Any suggestions is good.  I haven't tried it from the command line, maybe because I wasn't sure how to do it.

What did you mean appending it with s;. ???  At the end of my ascii key?  Can you give me an example please?

---

### Post by kolisikepu on 2008-04-16
How is it that I go to configure my wireless via the command line, but it say's "wlan0 ; No such device."

But yet, I can pick up wireless AP's through the gui.

Anyone...??

---


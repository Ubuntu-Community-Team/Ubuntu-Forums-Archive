---
title: "iwconfig wlan0 rate 11M"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by pHreaksYcle on 2008-03-29
Running Hardy Heron Beta although it is not a Hardy specific question so it can go here.

What are the consequences of running "iwconfig wlan0 rate 11M"? What exactly does it do? How do I know what number I specifically should use instead of 11? Someone from the site that I work on said that it made his wireless faster and more stable seemingly, because before he ran that, his speed was 1M as told by connection information on network-manager's left-click window. Any advice would be appreciated!

---

### Post by pHreaksYcle on 2008-03-29
Bump, being patient haha

---

### Post by pHreaksYcle on 2008-03-29
Running Hardy Heron Beta although it is not a Hardy specific question so it can go here.

What are the consequences of running "iwconfig wlan0 rate 11M"? What exactly does it do? How do I know what number I specifically should use instead of 11? Someone from the site that I work on said that it made his wireless faster and more stable seemingly, because before he ran that, his speed was 1M as told by connection information on network-manager's left-click window. Any advice would be appreciated!

Edit: I also have a thread in Beginner section, but it's not getting any play so I won't take up resources there, I will leave it here in the correct spot.

---

### Post by vargasman on 2008-03-29
Here's a link to some info about the iwconfig command. [http://linux.die.net/man/8/iwconfig ]("http://linux.die.net/man/8/iwconfig")

Here's a bit form the site about rate. 

rate/bit[rate]
    For cards supporting multiple bit rates, set the bit-rate in b/s. The bit-rate is the speed at which bits are transmitted over the medium, the user speed of the link is lower due to medium sharing and various overhead. You may append the suffix k, M or G to the value (decimal multiplier : 10^3, 10^6 and 10^9 b/s), or add enough '0'. Values below 1000 are card specific, usually an index in the bit-rate list. Use auto to select automatic bit-rate mode (fallback to lower rate on noisy channels), which is the default for most cards, and fixed to revert back to fixed setting. If you specify a bit-rate value and append auto, the driver will use all bit-rates lower and equal than this value.
    Examples :
    iwconfig eth0 rate 11M
    iwconfig eth0 rate auto
    iwconfig eth0 rate 5.5M auto 

You can also find this via the man pages.

```
man iwconfig
```

---

### Post by plucky on 2008-03-29
@pHreaksYcle,

From a terminal use ```
man iwconfig
``` will show you what iwconfig "wlan0 rate 11M" does.

Good Luck

---


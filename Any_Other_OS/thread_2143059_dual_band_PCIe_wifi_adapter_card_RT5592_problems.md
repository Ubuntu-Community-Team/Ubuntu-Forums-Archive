---
title: "dual band PCIe wifi adapter card RT5592 problems"
date: 2013-05-07
forum: Any Other OS
---

### Post by wednesday allfather on 2013-05-07
I'm having trouble getting my Rosewill N600PCE card working.  I'm hoping there is a guide somewhere that someone can point me to or a driver that works I just somehow missed after a day trying drivers and reading SERPs.  I'm running a pretty much stock "Mint" that is about 2 days old.  This is a new build, so I thought I would give Mint a try.  The juicy details follow:

The chipset is Ralink RT5592.  It seems to work, here is my "lspci" output for it:

```
03:00.0 Network controller: Ralink corp. Device 5592
```

This is the only driver I found that even kinda worked, but could not connect to the router

[HTML]http://rosewill.com/support/Support_Download.aspx?ids=3_145_362_2322&flag=d[/HTML]

Here is my "uname -a" output

```
Linux testbench 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

I was able to get the card controlled by the network manager, but I was never able to see any networks.  

I'm happy to post any additional info needed and thanks in advance for any help!

---

### Post by dbd on 2013-09-15
I'm thinking of getting a card with this chipset, did you ever get it working?

---


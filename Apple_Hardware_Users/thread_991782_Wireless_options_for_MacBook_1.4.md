---
title: "Wireless options for MacBook 1.4"
date: 2008-11-24
forum: Apple Hardware Users
---

### Post by mattgaunt on 2008-11-24
Hey everyone

I am having problems with WPA2 Enterprise encryption with the wireless drivers that come with hardy heron.

The drivers I'm currently using are the restricted Broadcomm drivers that ubuntu suggests.

I know it suggests using ndiswrapper on [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

But im unsure if this is appropriate for hardy heron, does anyone have any suggestions?

Gaunt

---

### Post by beauman on 2008-11-24
You are talking about the MacBook 4.1, right? Maybe you can try with
an update to Intrepid? Wireless will work out of the box. I have used
it a lot on my MB 4.1 lately, both with wep and wpa. No problems.
But I'm not sure, what Enterprise encryption exactly is, so I hope I could
help.

---

### Post by mattgaunt on 2008-11-24
Nah the drivers out of the box - the restricted ones, are the ones that break my ubuntu install when using the wireless encryption at uni.

I've just installed the ndiswrapper wireless drivers to see if that'll make a difference.

We'll see 2moro

---

### Post by _mario_ on 2008-11-24
> **mattgaunt said:**
> Nah the drivers out of the box - the restricted ones, are the ones that break my ubuntu install when using the wireless encryption at uni.

I've just installed the ndiswrapper wireless drivers to see if that'll make a difference.

We'll see 2moro
does it crash your system? if so you'll most likely want to have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=914697&highlight=wireless"). the bottom line is: ndiswrapper is the only solution then.

ciao,
Mario

---


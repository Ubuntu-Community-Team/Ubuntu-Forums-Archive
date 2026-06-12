---
title: "iwlist and iwconfig?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-12-18
Here goes my story:

A week or two ago, I upgraded to Hardy on my laptop. Things went bad thereafter however, and I was unable to open the network admin window. There is a thread in these forums on this bug and a report on launchpad too. Anyways, I first didn't know it didn't work and changed my wireless key.

That was the start of it all. I couldn't connect to the net after changing the key. I tried to launch the network admin to change the settings but like I said it failed. After several tries with kwifi, wpa_supplicant, wpa_supplicant gui etc, I gave up.

Today I took the computer back on my laps and tried again, this time with the new idea of iwlist and iwconfig.

So I went ahead and did a
```
iwlist scan; sudo iwconfig device_id "essid" s:pass_in_ascii; sudo ifup device_id
```
I was thinking of saving this as a shell script and setting it to run with each boot, but guess what; the network manager came back to life and asked me for the pass for the network! I was both shocked and happy to see this, and after entering the password I was connected to the internet.

My question now is, although this magic somehow worked, why wasn't I directly connected to the net and instead the network manager came up and asked me for password? Where did I go wrong, or is there a bug in iwconfig (I doubt there is one in such a popular and widely used program)?

---

### Post by Siph0n on 2007-12-18
Gutsy just came out, why upgrade to an unstable release??? I think your best bet is to go back to Gutsy... Hardy is no where near ready (I Think)

---

### Post by Majorix on 2007-12-18
I am fine with Hardy, I have tested Gutsy since its Alpha releases too, and I can USUALLY solve my problems, so like I said there is nothing wrong with choosing Hardy over Gutsy. Good thing, you get all the latest software. But thanks for the advice.

---


---
title: "wireless help"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by antonio_ing on 2007-10-18
I started this morning to check my wireless card because i'm not able to connect with that at home. Until yesterday I have been able to connect at my work. Maybe I've installed the wrong drivers. What can I do to delete everythin and put again the drivers of yesterday?

Can someone suggest me how I should configure my wireless card?

Thank you very much

---

### Post by mikeyphi on 2007-10-18
Could you post details of your wireless card - and also which version of Ubuntu you have?

---

### Post by dward526 on 2007-10-18
Two questions,
1) Does your work have an 'open' network?  
2) Does your home network use a security protocol (WEP, WPA)

When I had a similar issue, it was not my wireless at all, but the config of my home network

---

### Post by dward526 on 2007-10-18
this is a post just so i can subscribe,I forgot the last time

---

### Post by antonio_ing on 2007-10-18
It's an Ubunty Feisty Fawn 7.04

My wireless card is 

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)

---

### Post by antonio_ing on 2007-10-18
THe owner of the house bought to us a new router MAc airport base extreme. I don't exactly is is WEP or not

---

### Post by Lord_Dicranius on 2007-10-18
> **dward526 said:**
> this is a post just so i can subscribe,I forgot the last time
At the top of the thread, on the right there's a link that reads "Thread Tools".  Click on that, then select "Subscribe to this Thread" from the menu that drops down :)

---

### Post by antonio_ing on 2007-10-18
ok. I did it

---

### Post by mikeyphi on 2007-10-18
> **antonio_ing said:**
> ok. I did it

Bravo!!

Could you post your fix - in case someone else has a similar problem?

---

### Post by antonio_ing on 2007-10-18
sorry. my fix?

---

### Post by antonio_ing on 2007-10-18
Now i've seen that ubuntu doesn't understand that I have a wireless card!!!! Help me
there was until yesterday...

---

### Post by dward526 on 2007-10-18
It does not see it with ifconfig?

---

### Post by dward526 on 2007-10-18
> **Lord_Dicranius said:**
> At the top of the thread, on the right there's a link that reads "Thread Tools".  Click on that, then select "Subscribe to this Thread" from the menu that drops down :)

Thank you...that is a lot easier...and not as rude ;)

---

### Post by brn on 2007-10-18
> 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
This isn't a wireless controller.  Try... ```
lspci | grep Nework
``` ...and post the result here.

---

### Post by antonio_ing on 2007-10-18
there is no post.

---


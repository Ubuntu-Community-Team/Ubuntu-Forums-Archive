---
title: "How do I upgrade properly?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-03-31
I have Ubuntu 6.06 installed on my machine. But I want to switch to 7.04 BETA.

Is there any way I can do this properly? Without formatting and stuff? Plus will I be able to switch to the official version of 7.04 from BETA?

---

### Post by justin whitaker on 2007-03-31
> **Majorix said:**
> I have Ubuntu 6.06 installed on my machine. But I want to switch to 7.04 BETA.

Is there any way I can do this properly? Without formatting and stuff? Plus will I be able to switch to the official version of 7.04 from BETA?

In the past, what you could do is change all the repositories from Dapper to Edgy, and do a dist-upgrade. I think you can still do that from Edgy to Feisty, but I would strongly suggest that you do not do that from Dapper to Feisty. Dapper and Feisty are two completely different animals, and you are probably better off starting from scratch. 

Once you have the beta installed, you are using the Feisty repositories, so when the Devs decide that the release is ready, you will be up to date.

---

### Post by r4ik on 2007-03-31
If you have got a working system i would wait until it goes final.

---

### Post by Majorix on 2007-03-31
Ah yes I was also going to ask if changing the repos would work. Thanks for clarifying.

Now I have to format the PC? Poof...

Thanks a lot.

@r4ik:
I want to install this asap because I have a few games that won't work under 6.06 but according to a source they will work under 7.04.

---

### Post by dmizer on 2007-03-31
upgrading from dapper to edgy is a shaky one.  you're likely to have lots of breakage, and end up with an unstable system.  it took me weeks to iron out all the kinks from my last dapper to edgy, and i'm still not sure it's completely recovered.  edgy to feisty was fairly shaky too.

your best bet is to create a home partition according to this page: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 

then burn a copy of feisty and install feisty directly.  when you get to the partition portion of the install, just be sure not to overwrite your home partition.  then, when completed, you can mount your old home partition and all your old settings will be imported.

---

### Post by Maestro23 on 2007-03-31
> **Majorix said:**
> I have Ubuntu 6.06 installed on my machine. But I want to switch to 7.04 BETA.

Is there any way I can do this properly? Without formatting and stuff? Plus will I be able to switch to the official version of 7.04 from BETA?

Upgrading to Feisty: [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

---


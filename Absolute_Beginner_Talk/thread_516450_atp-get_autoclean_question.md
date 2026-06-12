---
title: "atp-get autoclean question"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by rgd55 on 2007-08-03
When I use this code I get the following message,
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
rgd@feisty:~$ 

 Can someone advise please?

Thanks

---

### Post by heimo on 2007-08-03
Try
```
sudo apt-get autoclean
```

---

### Post by rgd55 on 2007-08-03
Sorry,I now see that I mispelled my thread title.
I used apt-get autoclean and the result was,
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
rgd@feisty:~$

---

### Post by heimo on 2007-08-03
> **rgd55 said:**
> Sorry,I now see that I mispelled my thread title.
I used apt-get autoclean and the result was,
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
rgd@feisty:~$

Ok. Did you use sudo in front of that command? Like:
```
sudo apt-get autoclean
```

---

### Post by rgd55 on 2007-08-03
yes I did

---

### Post by rgd55 on 2007-08-03
oh ,I did not use sudo.I give it a try.

---

### Post by heimo on 2007-08-03
> **rgd55 said:**
> yes I did

Close any other package management software, like Synaptic Package Manager, if open and retry.

---

### Post by rgd55 on 2007-08-03
yes it did work.
 Thanks

---


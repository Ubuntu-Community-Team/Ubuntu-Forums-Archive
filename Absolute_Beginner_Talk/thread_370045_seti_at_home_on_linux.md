---
title: "seti at home on linux"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by black1 on 2007-02-25
I was wondering. has anyone got the SETI @ Home project workin on linux and in Ubuntu? and was it possible with doing command line stuff?

years ago it was much easier to do on windows and macs and now it seems to be a bit more of a pain and also new to linux makes it even that more confusing.

thanks.

---

### Post by wpshooter on 2007-02-25
Consider giving **folding-at-home** a try.

You can help possibly find treatments and possibly cure for cancer and other medical problems.

It works great on Linux/Ubuntu.

Thanks.

---

### Post by Kateikyoushi on 2007-02-25
You have to enable the universe repository. Do it in system > administration > software sources. just tick the box.

Then copy the following line to the terminal.

```
sudo aptitude install boinc-app-seti
```

key in your password and it will install boinc.

---

### Post by dwblas on 2007-02-25
I'd suggest that you consider protein folding from Stanford instead [http://folding.stanford.edu/](http://folding.stanford.edu/)  Instead of looking for extraterrestials they are trying to find cures for diseases.  Teamubuntu is #45104 [http://fah-web.stanford.edu/cgi-bin/main.py](http://fah-web.stanford.edu/cgi-bin/main.py)

---

### Post by Talon2 on 2007-02-25
> **Kateikyoushi said:**
> You have to enable the universe repository. Do it in system > administration > software sources. just tick the box.

Then copy the following line to the terminal.

```
sudo aptitude install boinc-app-seti
```

key in your password and it will install boinc.

OP needs to be aware that this will get an very old version (v5.4) of BOINC that is missing features that are important if systems have thermal control issues.

As of right now, AFAIK, the only way to get the latest version (5.8) is to download it from the BOINC website and install it manually.

---

### Post by DarkDancer on 2007-03-05
hehe... ;)

[http://news.yahoo.com/s/ap/20070221/ap_on_hi_te/techbit_aliens_laptop](http://news.yahoo.com/s/ap/20070221/ap_on_hi_te/techbit_aliens_laptop)

---

### Post by Kateikyoushi on 2007-03-05
On some other site the headline was even mroe funny, Seti finally founds something. ;)

---


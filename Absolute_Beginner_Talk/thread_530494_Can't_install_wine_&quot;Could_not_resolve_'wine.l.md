---
title: "Can't install wine: &quot;Could not resolve 'wine.lowvoice.nl'&quot;"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by cam2009 on 2007-08-20
I had wine since I started using ubuntu, and it worked fine for months, but I think a recent update might have done something. Wine is no longer installed, and if I try to install it from Add/Remove, I get:

W: Failed to fetch [http://wine.lowvoice.nl/apt/pool/main/w/wine/wine_0.9.43~winehq0~ubuntu~7.04-1_i386.deb](http://wine.lowvoice.nl/apt/pool/main/w/wine/wine_0.9.43~winehq0~ubuntu~7.04-1_i386.deb)
  Could not resolve 'wine.lowvoice.nl'

And similar errors if I try to install from elsewhere. What could be the problem?

---

### Post by l33t_3lv3n_g33k on 2007-08-20
Wine is at a different repo now.  According to [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")
you should run the following for a Feisty install:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```

---

### Post by cam2009 on 2007-08-20
> **l33t_3lv3n_g33k said:**
> Wine is at a different repo now.  According to [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")
you should run the following for a Feisty install:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```
Woohoo, thanks. Worked great.

---

### Post by Speedoo on 2007-09-25
Funny, I have the same problem.  But when I tried the code you posted, I got  the error "could not resolve /wine.lowvoice.nl" again.  Any other suggestions?
Thanks,

---

### Post by Speedoo on 2007-09-25
Oops, figured it out.  I had to comment out 'wine.lowvoice.nl' from my sources.list.  It appears it was placed there by Automatix 2.  All is well now.  Thanks again!

---

### Post by TheSlayerIsBack on 2007-10-23
> **cam2009 said:**
> I had wine since I started using ubuntu, and it worked fine for months, but I think a recent update might have done something. Wine is no longer installed, and if I try to install it from Add/Remove, I get:

W: Failed to fetch [http://wine.lowvoice.nl/apt/pool/main/w/wine/wine_0.9.43~winehq0~ubuntu~7.04-1_i386.deb](http://wine.lowvoice.nl/apt/pool/main/w/wine/wine_0.9.43~winehq0~ubuntu~7.04-1_i386.deb)
  Could not resolve 'wine.lowvoice.nl'

And similar errors if I try to install from elsewhere. What could be the problem?

well i got it working man thanks, but how do i install exe files

---


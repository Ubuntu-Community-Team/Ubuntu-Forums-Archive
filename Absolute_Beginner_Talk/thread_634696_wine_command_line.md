---
title: "wine command line"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by th1bill on 2007-12-08
Every time I download the deb package esword-ubuntu_1.6_al... from my user account I get the single choice of using GDebi to unpack it and it does not work.  If I do the deed from my root account all goes perfectly except that I do not have access to the application from my user account.  Under my root acct it uses wine to unpack the deb.  Is there a command line I can use in the Terminal to use wine and get the package or is there a way to select wine from the other option in the drop down of the download configuring app that comes up?

Willis Taylor
Killer Spade 806
CE 1968, 1969

---

### Post by nikoPSK on 2007-12-08
have you tried:
```

sudo apt-get install wine
```

rather than the deb?

---

### Post by th1bill on 2007-12-08
> **nikoPSK said:**
> have you tried:
```

sudo apt-get install wine
```

rather than the deb?

Ok, I did and when I try to download the package it uses GDebi.  Same problem.

---

### Post by th1bill on 2007-12-08
Can I uninstall GDebi?

---

### Post by nikoPSK on 2007-12-08
y would would you want to?

---

### Post by th1bill on 2007-12-08
> **nikoPSK said:**
> y would would you want to?

So I can use wine to unpack this package.  I just did so and I'm about to attempt it.

---

### Post by th1bill on 2007-12-08
I tried it and now the Archive Manqger is the default.  There is a way around this and I just do not know the command line because wine has been installed the entire time.

---

### Post by nikoPSK on 2007-12-08
sorry, I'm a bit lost here.... You want to remove gdebi so you can unpack it with wine...?

---

### Post by th1bill on 2007-12-08
> **nikoPSK said:**
> sorry, I'm a bit lost here.... You want to remove gdebi so you can unpack it with wine...?

I tried that and it still did not go to wine so I have reinstalled GDebi.  The e-Sword must run under wine and the directions I recall said it must be installed with wine to run.  When I install it in the root it does the unpacking and installing in wine, however, I am un able to use the program in anything but the root account and that is just no desirable at all.  I need to install from the user account to be able to access it to do my ministry work and get off the Windows machine completely.

---

### Post by th1bill on 2007-12-08
I'm sorry if I seem strange but I've been at this for four days now and there has to be a command line to do the job with wine and I just cannot find it and GDebi does not work at all.

---

### Post by nikoPSK on 2007-12-08
would you be willing to do a clean install? I'm not recommeding it but if you want to....

---


---
title: "inittab - needed for install of Oracle 11G"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by bzachd on 2008-02-18
Hi,

Did some research on inittab before posting. I am doing an install of Oracle 11G and its looking for the inittab in etc... if I copy one of the examples from this site, where people have posted their inittab files, will that cause me any issues? I see that no inittab is located in the directory where Oracle is looking. Any advice would be helpful.

One other question, I have installed the telnet application.... what command runs it so I can configure my user name and passwords. If possible directory would be very helpful.

Thanks,
Zach

---

### Post by freelinuxhelp on 2008-02-20
I recommend using ssh instead of telnet. SSH provides encryption, whereas telnet transfers everything in clear text.

As for the inittab, I've just noticed that my machine doesn't have an inittab, which is really weird to me. It should be in /etc/
I don't know if I would just download one. Try to create a blank one in /etc/

```
sudo touch /etc/inittab
```

---

### Post by scxtt on 2008-02-20
inittab tends to be more specific to redhat based distros ... my guess is that oracle uses it to determine what run-levels it should run under ... coping a default one shouldn't do you much harm, tho i believe ubuntu boots into run-level 2 and most rpm-based distros (i'm looking at centos5) boot into run-level 5 -- strictly speaking about X ... just something to think about ...

and i 2nd [COLOR="DarkGreen"]ssh[/COLOR] over [COLOR="Red"]telnet[/COLOR] ...

---

### Post by freelinuxhelp on 2008-02-21
That explains why I don't have an inittab. I've been on RH/Fedora/CentOS since around 1998. Just switched to Ubuntu when Gutsy came out.

---

### Post by bzachd on 2008-02-21
scxtt, freelinuxhelp

Thanks for the great advice, SSH it is, and thanks again for informing me about the inittab.

Thanks again,

Zach

---

### Post by kokiri on 2008-02-21
ubuntu did have inittab up until 6.10, the new initng replaced it and massively sped up boot times due to initng being multitasking and the old inittab being sequential

---

### Post by freelinuxhelp on 2008-03-08
Glad to know why it's missing.
Did you ever get this working?

---


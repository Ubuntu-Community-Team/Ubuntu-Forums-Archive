---
title: "My only proper user account is broken"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by chris90uk on 2007-01-06
I installed some themes from gnome-look and art.gnome as per the instructions on these forums, but then it crashed after I chose an icon theme. Therefore, I presume it has selected this icon theme. Now I can't log on to that account, it just freezes on an Ubuntu orange background with the mouse cursor on it. I can't do anything else on the computer - the only other account on the computer can't sudo for some reason because it's a guest account probably. ](*,) 

Any ideas on how to restore my system? I am posting this from the guest account!

---

### Post by riven0 on 2007-01-06
Why don't you try re-installing the ubuntu desktop? Go back to the login screen, click Sessions >> Failsafe Terminal.

Then log in if you have to do and do:

> sudo apt-get install --reinstall ubuntu-desktop

---

### Post by teaker1s on 2007-01-06
or failsafe terminal login as root
[COLOR="Red"]startx[/COLOR]

and just create a new account and reboot;)

login to your new account and the command below will give root access to copy your files over
[COLOR="Red"]**gksudo /usr/bin/nautilus **[/COLOR]

---

### Post by riven0 on 2007-01-06
That's a better way to do it! :p Try that first.

---

### Post by chris90uk on 2007-01-06
Thanks for your help, I'm back into my user account. Now, how do I go about removing the icon themes/other themes from my system? Thanks.

---

### Post by aysiu on 2007-01-06
> **chris90uk said:**
> Thanks for your help, I'm back into my user account. Now, how do I go about removing the icon themes/other themes from my system? Thanks.
```
rm -r ~/.themes/*
rm -r ~/.icons/*
gnome-theme-manager &
```

---

### Post by omockler on 2007-03-14
Im having about the same problem.

Will doing this reinstall the entire system?

> **riven0 said:**
> Why don't you try re-installing the ubuntu desktop? Go back to the login screen, click Sessions >> Failsafe Terminal.

Then log in if you have to do and do:

---

### Post by Famicommie on 2007-03-14
> **omockler said:**
> Im having about the same problem.

Will doing this reinstall the entire system?

No.

---


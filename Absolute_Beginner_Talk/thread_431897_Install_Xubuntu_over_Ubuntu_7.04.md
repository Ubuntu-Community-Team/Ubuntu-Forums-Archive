---
title: "Install Xubuntu over Ubuntu 7.04"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2007-05-03
I have 7.04 on my Thinkpad T23. The laptop is getting old, and while it ran Edgy fine, I notice 7.04 is considerably slower. I guess the machine can no longer handle it.

I'd like to install Xubuntu.

Can I install it over the top of Ubuntu (not dual boot) like you do when you upgrade from Edgy to Feisty. So I don't have to change my Home folder my settings and everything. Or do I have to do a new install and lose everything (except if I back up my Home folder).

Tweedicus

---

### Post by Iarwain ben-adar on 2007-05-03
Hi there,

even easier!
```
sudo aptitude install xubuntu-desktop
```

That will install XFCE with all the programs attached to it :D

(just select XFCE from the 'sessions' menu before logging in ;)


Iarwain

---

### Post by starcraft.man on 2007-05-03
> **Tweedicus said:**
> I have 7.04 on my Thinkpad T23. The laptop is getting old, and while it ran Edgy fine, I notice 7.04 is considerably slower. I guess the machine can no longer handle it.

I'd like to install Xubuntu.

Can I install it over the top of Ubuntu (not dual boot) like you do when you upgrade from Edgy to Feisty. So I don't have to change my Home folder my settings and everything. Or do I have to do a new install and lose everything (except if I back up my Home folder).

Tweedicus

Sounds fine to me if you just install xubuntu back over the old / (root), old swap file and home should be reusable. Have fun with Xubuntu.

Or you can do what he said above, don't forget to remove ubuntu-desktop after, since you won't need it...

---

### Post by Tweedicus on 2007-05-03
Thank you,

Three questions.

1.) How do I remove Ubuntu Desktop

2.) When  I have removed it will the computer automatically login to Xubuntu when I log in without selecting it.

3.) Will everything, including my settings still be there when I remove the Ubuntu Desktop and transferred to Xubuntu.

Thank you

---

### Post by starcraft.man on 2007-05-03
Easy to remove ubuntu-desktop, just type this into terminal

```
sudo aptitude remove ubuntu-desktop
```

sudo aptitude remove followed by any program is the generic way to remove things by terminal, if you switch remove with install then your installing :).

2) I think you should, when you log in it will be one of the options in session. If its not default, you can just make it default after selecting it at log in.

3) I think most of your program settings should be the same... could be wrong, i never used the xubuntu desktop.

Have fun with your new XFCE :D

---

### Post by Tweedicus on 2007-05-03
Thanks for that. I like working in Terminal, just have to learn all the commands.

Tweed

---

### Post by starcraft.man on 2007-05-03
> **Tweedicus said:**
> Thanks for that. I like working in Terminal, just have to learn all the commands.

Tweed

No problem, have fun tweed, don't be shy to ask any more questions :)

---

### Post by PatM on 2007-05-03
> **Iarwain ben-adar said:**
> Hi there,

even easier!
```
sudo aptitude install xubuntu-desktop
```

That will install XFCE with all the programs attached to it :D

(just select XFCE from the 'sessions' menu before logging in ;)


Iarwain

I followed the instructions and it worked fine for xubuntu.

When I tried to do this with kubuntu, however, it wouldn't work.
How can I add Kubuntu choice to Ubuntu?

PatM

---

### Post by Iarwain ben-adar on 2007-05-04
PatM,
just replace xubuntu with kubuntu
=>
```
sudo aptitude install kubuntu-desktop
```


iarwain

---


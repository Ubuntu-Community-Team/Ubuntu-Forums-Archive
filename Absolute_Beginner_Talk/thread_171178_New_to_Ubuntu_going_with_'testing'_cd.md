---
title: "New to Ubuntu: going with 'testing' cd"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by jeckil on 2006-05-06
Hi all

I Decided to check this new distro out. 


I have never tried a 'testing' version before, im more of a linux n00b than an expert. 

I will install the testing version 6.06 for this distro, i personally dont foresee any problems since my hardware is about 6 months /1 year current. 

I have a few questions though:

What will the procedure be to upgrade to the stable version once its out in june? Will i have to reinstall it thus destroying my data or will there be a simple 'mouse click' solution to this?

Im not a big fan of recompiling kernels since i mostly dont know what im doing. But if its likely to happen in this scenario will there be a lot of support on this site? 

Thanks for your attention

---

### Post by manicka on 2006-05-06
Just keep updating with Synaptic and you will have the final release

at the cli you would run

```
sudo apt-get update
sudo apt-get upgrade
```

to achieve the same thing

You won't need to manually upgrade the kernel as apt-get or Synaptic will take care of this for you

---

### Post by htinn on 2006-05-06
You only need to recompile kernels if you have to configure them for special purposes (which you probably don't need to worry about).

---

### Post by jeckil on 2006-05-06
Cool! Thanks Guys? Does this also apply to the 5.10 Version?

---

### Post by ds[de] on 2006-05-06
Yes it does; you'll just have to change 'breezy' to 'dapper' in your /etc/apt/sources.list

Regards,
ds[de]

---

### Post by Sef on 2006-05-06
If you change your sources then to upgrade to via the command line is this:

sudo apt-get update

sudo apt-get dist-upgrade

---


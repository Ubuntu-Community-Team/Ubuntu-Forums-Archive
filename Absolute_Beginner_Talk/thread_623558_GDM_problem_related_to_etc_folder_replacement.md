---
title: "GDM problem related to /etc folder replacement"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-11-26
Here is the situation:

I backed-up my /etc folder from my ubuntu 7.04 machine and put in the brand new XUBUNTU 7.10 machine using live CD.

Then I wanted to run Xubuntu machine and here is the error at booting:


> 
Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but i snot owned by user 106 and group 111. Please correct the ownership or GDM configuration and restart GDM 

 I am stuck. I am not an expert and desperately need help.
If any one describe me what I should do in detail, I will really appreciate.

I just wanted to use setting from old machine on my new machine. is this too much!!!!

---

### Post by tesserhex on 2007-11-26
Hi,

First, open up a terminal window and check the owners permissions with

```
ls -ld /var/lib/g*
```

Should display something like:-

drwxr-xr-x 2 root root 4096 2007-10-16 /var/lib/gjc-4.2
**drwxr-x--- 2 root gdm 4096 2007-10-16 /var/lib/gdm**

If the GDM entry (in bold, above) says it's owner is anything other than 'root', you can reset the permissions with:-

```
sudo chown root /var/lib/gdm
```

Not got experience of this issue, so this is conjecture... let me know how it goes.

---

### Post by tesserhex on 2007-11-28
Happy to help!

---

### Post by mozkaynak on 2007-11-28
Thanks alot tesserhex.
actually your method worked.

---


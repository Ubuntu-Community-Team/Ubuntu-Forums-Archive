---
title: "Problem while loading &quot;OAFIID:GNOME_FastUserSwitchApplet"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Joeyscout on 2007-11-21
:confused:I haven't been able to find an answer to my problem using these threads. But I am new at this as well. I have Been trying to install Ubuntu 7.10 and have encounted the following Error message.

[COLOR="Red"]The panel encountered a problem while loading "OAFIID:_FastUserSwitchApplet[/COLOR].

I have tried Don't delete but the whole system has taken forever to load over 24hrs. Is it worth deleting?????

Help pleeZ :confused:

---

### Post by aroch1 on 2007-11-21
Yes delete it, you can access the same functionality by logging out and in as another user.

To fix this problem more permanently, try
```
sudo aptitude install gnome-applets
```

---

### Post by Duckstar on 2007-12-31
I also have this problem.
I am trying to install Ubuntu (7.10) on a clean machine and every time i boot up into the try and install bit it comes up with this error message.  At first i thought it was the CD so i burnt another 2 copies of it and tried with the same result.  If i press delete it just disappears, if i press don't delete it just disappears.  When i try to click install it allows me to select it but doesn't seem to open it.
I have tried pressing enter to select it and by right clicking and selecting open.  I also tried above by logging in and out. 
I just seem to be lagging badly.  Any ideas how i can get this installed ? 
Thanks in advanced
Duckstar

---

### Post by Green Bean on 2008-02-08
I also have just run into this with a fresh install of ubuntu 7.10 server 64amd on a new Dell Dimension 9200 - and with the gnome / X ui installed on top.  I tried sudo aptitude install gnome-applets, but it reported no files needed updating / installing.  Unfortunately (after loging in) my Dell USB keyboard doesn't work so I can't even press the delete or don't delete option.  I'm a newbie to linux.

So I'll appreciate trying out solutions others may have to this ...

---

### Post by Green Bean on 2008-02-08
Addendum - I wasn't able to use my Microsoft Wireless mouse to select the don't delete / delete options, and at that time I found that the Dell keyboard wasn't working - literally no keys did anything.  So I just tried another non-wireless mouse, and was able to click on the "delete" button.  Then keyboard functionality returned, and I was able to use gnome as usual.

---

### Post by Shailen Sobhee on 2008-03-20
On Fedora 8:

```
yum install -y fast-user-switch-applet
```

solved the problem :)

---

### Post by woaiwojia on 2008-04-10
sudo aptitude install gnome-applets

---

### Post by bjornb on 2008-07-07
installing the gnome-applets and the fast-user-switch-applet solved these problems for me too.

---


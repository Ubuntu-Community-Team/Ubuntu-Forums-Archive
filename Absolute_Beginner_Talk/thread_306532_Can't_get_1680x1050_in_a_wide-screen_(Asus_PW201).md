---
title: "Can't get 1680x1050 in a wide-screen (Asus PW201)"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by xeo_pt on 2006-11-25
I just get a Asus PW201 to work with Ubuntu 6.10
but it works only in 1280x1024 as my 17" LCD.
When I configure the xserver as in
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

the Xserver crashes.

Any one as try to do the same?

Thanks in advance.

---

### Post by Ecthelion on 2006-11-25
>  I just get a Asus PW201 to work with Ubuntu 6.10
but it works only in 1280x1024 as my 17" LCD.
When I configure the xserver as in
[https://help.ubuntu.com/community/Fi...esolutionHowto](https://help.ubuntu.com/community/Fi...esolutionHowto)

the Xserver crashes.


Hey,
When exactly does the x-server crash?
While doing the dpkg-reconfigure xserver-xorg?
If so, try doing it like this:
Press ctrl-alt F1
do:
```
sudo /etc/init.d/gdm stop
```
This will stop manually your running xserver
then do the:
```
sudo dpkg-reconfigure xserver-xorg
```
And after that do
```
sudo /etc/init.d/gdm start
```
to restart your xserver.

If you are using kde, then type /etc/init.d/kdm instead of /etc/init.d/gdm

I hope this helps...

---

### Post by xeo_pt on 2006-11-30
Thank you for your help, but I change monitor,
now I have a Apple Dysplay Cinema 23" 
and I'm starting to adjust Ubuntu to use it.

---


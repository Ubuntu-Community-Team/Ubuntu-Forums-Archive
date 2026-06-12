---
title: "how to re enable admin user"
date: 2012-09-21
forum: Any Other OS
---

### Post by THIRI MARLAR on 2012-09-21
I use ZORIN 6 and by mistake unable my admin user account. I tried to re-eneble but it does not recognize my password anymore. How can I re-enable it? I am using now a standard user account without password.
thanks a lot

---

### Post by Deepak A on 2012-09-21
Are talking about root account?

you can reset it from recovery mode. For that, you need to reboot and boot into recovery mode(Also known as single user mode). open a terminal from there and just type *passwd* 
And enter the new password for root. hope it may work.... 


Deepak

---

### Post by NikTh on 2012-09-21
Hi , 

**1.** Check if you can use the Console mode 

Press Alt+Ctrl+F2 and try to login from there. If you succeed then give this command 
```
sudo passwd username
```replace username with yours. 

**2.** If above not working , then try this : [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
to reset your password. 

When you reset your password I assume you will have the ability to change user's account. 

Thanks

---

### Post by newb85 on 2012-09-21
Aw, you beat me to it, NikTh.

---

### Post by THIRI MARLAR on 2012-09-23
I am using ZORIN 6 and by mistake disabled my admin account. Now that I try to re-enable it does not recognize the password (and I am sure of my password). How can I re-enable the administrator account, when I try I get the message log on as a super user..etc..
Thanks

THIRI MARLAR

---

### Post by overdrank on 2012-09-23
Threads merged.

---


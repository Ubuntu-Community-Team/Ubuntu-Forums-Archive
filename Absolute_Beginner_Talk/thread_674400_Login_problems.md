---
title: "Login problems"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by truKrewl on 2008-01-21
Hey all,

After configuring Samba using this guide [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto), I cannot log in to the machine using UBUNTU 7.10. Everytime I try to login, I get a login failure message. :confused:

I have been through the recovery mode and logged in as root, and made sure that the username existed and changed the password for it, but still the problem persits.

Any ideas why this may be occuring? Have I configured the files incorrectly? Or forgot to do something???

I am a complete UBUNTU newbie (have only been using it for two days), so any help will be much appreciated! :)

Thanks in advance

truKrewl.

---

### Post by dstew on 2008-01-21
That is a really tough HowTo. Do you really want to use the Active Directory system?

In the HowTo, it says after you have set it up, you need to login a special way, using both your domain and password:> Usage

Logon with DOMAIN+USERNAME, unless you included "winbind use default domain" in your smb.conf, in which case you may log in using only USERNAME.

login: LAB+manuel
Password: *****
...
LAB+manuel@linuxwork:~$



---

### Post by truKrewl on 2008-01-22
Hey dStew and thanks for your quick response!

Yes, when the How to instructed to log in with domain and username I did. But still login failure :( I inputted the login exactly as 'DOMIAN + USERNAME' where DOMAIN is mycompname and USERNAME is my AD username.

I tried logging in with the username I created when installing Ubuntu, and with another username I had set up to no avail! :confused:

One thing I did notice is if I give the correct username and a wrong password it says wrong password, however when I supply the correct login details it says login failure (or incorrect can't remb - soz)??? Is this any help???

Also, I have got nearly everything to work by following the HowTo article I posted in my first post, but when I try to connect from my windows machine to the Ubuntu server, it gives me a login prompt. I supply login details and the login box reappears again - no login failure message or no other message for that matter at all. Any idea why this may occur???

---

### Post by dstew on 2008-01-22
I don't think I can help you too much more at this point. I really don't have any experience with the Active Directory system, only with Windows sharing. There are some other Ubuntu forums you might try posting in. The Networking and Wireless forum has a number of threads on the Active Directory system. You might find people there who have experience, and you could email them. Best wishes and good luck.

---

### Post by truKrewl on 2008-01-22
No worries and thanks dstew for your help, I will take your advice and try one of the other forums!

---


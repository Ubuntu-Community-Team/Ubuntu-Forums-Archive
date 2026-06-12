---
title: "gdebi-gtk problem with root"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by dfinf2 on 2007-04-30
I get this error whenever I try to install the easy Ubuntu package, it also happens when trying to install codecs for audio, too. New to Linux so I am not quite sure what it means and I searched to find an answer but I could have missed it. Some help would be great! 
Thanks 

```
Failed to run gdebi-gtk '--non-interactive' '/home/metheuser/Desktop/easyubuntu_latest.deb' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
```

---

### Post by rmt on 2007-04-30
You may need to run it with "gksudo" for gnome or "kdesudo" for KDE

---

### Post by zvacet on 2007-05-01
Do you have two accounts,one with administrator privileges ans second as desktop user?If I´m right you can not install if you don´t have superuser privileges.That mean your file wich you want to install must be in your administrator account.

---

### Post by dfinf2 on 2007-05-01
I only have the one account I, created it when I installed Ubuntu. There shouldn't be another user. So I assume I have Super User privelages. Well if worse comes to worst I will just reinstall it and try again. Not really a big deal just time consuming. Thanks for the help so far.

---


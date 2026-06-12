---
title: "How to dual boot ubuntu and mac os without refind?"
date: 2020-09-12
forum: Apple Hardware Users
---

### Post by lzy917 on 2020-09-12
[COLOR=#242729][FONT=Arial]I'm trying to install ubuntu on my MacBook air 2019 with Catalina 10.15.6. But my MacBook has the secure boot feature which doesn't allow refind to work at all and I'm not feeling comfortable to disable secure boot, so is there any way to dual boot without refind?[/FONT][/COLOR]

---

### Post by gsahli on 2020-09-12
I don't have Catalina installed, but I see this addressed here:
[https://sourceforge.net/p/refind/discussion/general/thread/1a96f5bd6d/?limit=25](https://sourceforge.net/p/refind/discussion/general/thread/1a96f5bd6d/?limit=25)

---

### Post by gomie on 2020-11-06
Disable Secure Boot prior to installation, through Recovery Mode > Terminal "csrutil disable"
After refind is installed, reverse the operation > Terminal "csrutil enable"
[http://www.rodsbooks.com/refind/sip.html#disable](http://www.rodsbooks.com/refind/sip.html#disable)

---


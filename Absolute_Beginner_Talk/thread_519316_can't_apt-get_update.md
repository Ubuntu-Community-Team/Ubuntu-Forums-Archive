---
title: "can't apt-get update"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by ncwalker on 2007-08-06
Can't apt-get update 

--------------------------------------------------------------------------------

Hi everyone, 

I am using a terminal window and logging in as root and attempting

apt-get update

and I am getting

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
Could not resolve 'security.ubuntu.com'

and a series of other similar errors. Can anyone help me 'resolve' this 

On a potentially related note I can't get Apache to load (either from Webmin or manually)

I also have noticed that the li command no longer works when I am in terminal window. 

It says: 

The program 'li' is currently not installed. You can install it by typing sudo apt-get install limo
Make sure you have the 'universe' component enabled
bash: li: command not found

When I enter sudo apt-get install limo I get a warning that the package cannot be authenticated. When I tell it to install without verification it says it cannot resolve 'ca.archive.ubuntu.com'

Please help! I have been stuck here all day!

---

### Post by Inxsible on 2007-08-06
1) are you sure your internet is working?

2) it sometimes happens, that the repositories that you are trying to hit are down or busy. Try after some time.

3) have you checked all urls to be correct?

---

### Post by inwivled on 2007-08-06
maybe your DNS is not working

---

### Post by ncwalker on 2007-08-06
The internet appears to be working, 

What would I check for to see if the urls were working?  i.e.  when I look in my /etc/apt/sources.list and copy the url out of that file what should I see on the browser when I enter that?

Could someone post a relaible sources.list file?

---

### Post by ncwalker on 2007-08-06
inwivled  Thanks for the response.  How can I check if my DNS is working ?  

Thanks!

---

### Post by irish_flu on 2007-08-06
> **ncwalker said:**
> inwivled  Thanks for the response.  How can I check if my DNS is working ?  

Thanks!

If you can get to websites using names like "www.google.com", your DNS is working.  If it weren't, you wouldn't be able to resolve "www.google.com" and you'd have to use the IP address (like "123.45.67.89") to get there.

I'm gonna guess that maybe there's one non-stock repository in your sources.list that is down; maybe the file (somebody will hopefulyl correct me on this if I'm wrong) is trying to check that first, then not getting to the other repositories after that fails?

---

### Post by Gremlinzzz on 2007-08-06
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by alienexplorers on 2007-08-06
You did not load Automatix and let it mess with your source list did you?

---

### Post by ncwalker on 2007-08-07
No Automatrix used.

I got it!

A friend helped me set up DNS 

I typed ```
sudo vi /etc/network/resolv.conf
```
and then added 

```
nameserver 208.67.220.220
nameserver 208.67.222.222
```

to the top of the file and then 

```
sudo /etc/init.d/dns-clean start
```

to make sure there weren't any  leftover addresses cached 

It's working now

Thanks benanzo!

---

### Post by Inxsible on 2007-08-07
Cool. Dont forget to mark your thread as solved :)

---


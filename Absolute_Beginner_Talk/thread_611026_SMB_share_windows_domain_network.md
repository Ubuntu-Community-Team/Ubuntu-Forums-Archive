---
title: "SMB share windows domain network"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by apegrape on 2007-11-12
Hello!

I am trying to serve a smb share on a windows domain. I got everything working so far except when I try to access the server via XP I get a prompt asking for domain/username if I enter in mshome or workgroup it does not work. There is too much involved to get the smb share to work thru AD so I just want a simple login samba1/passwd will do fine. I am not sure what I am doing wrong?

Thanks

dapper drake 6.06 LTS

---

### Post by reckless2k2 on 2007-11-12
you need to look at the samba docs about creating a samba username and password.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

the samba useranme and password has nothing to do with the user/pass on the machine that logs in.

---

### Post by apegrape on 2007-11-12
I created the user name and passwd thats not the problem. The problem is it wants a domain or workgroup or something? I just want a login and pass to work there is no domain to auth against.

[http://www.clarku.edu/intranet/images/loginbox.gif]("http://www.clarku.edu/intranet/images/loginbox.gif")

looks like that but it does nothing no matter what i enter in. If I mount the share on another linux machine it works fine.

---

### Post by reckless2k2 on 2007-11-12
sorry i'm not qualified to answer this one. i'm sure someone can chime in. if you are in a 2000/2003 domain, you do have to do a little tweaking in the smb.conf to get in the domain to serve on it though if i'm not mistaken. might be as simple as a hostname in the machine though. 

sorry i haven't played with that. hahaha.

---

### Post by apegrape on 2007-11-12
No problem.

I have the hostname setup, I can find the server on a windows machine fine. I just can't login because it expects a domain?

---

### Post by reckless2k2 on 2007-11-12
no i'm sorry i mean thee hostname in the conf. i remember some bits about domain stuff related to how you present your hostname.

---

### Post by Iowan on 2007-11-12
Check the **/etc/samba/smb.conf** to verify that the **workgroup=** line matches your windows machine (mshome?).

---

### Post by ed_d on 2007-11-12
Are both machines on the same domain? I ran into that before. Also, do you have the client piece installed under Ubuntu? you may have to tweak the smb.con file to allow you to access.

---

### Post by apegrape on 2007-11-12
well the way the network works linux and osx machines do not auth with AD. This shouldnt be a problem since any machine can get on the network regardless if you're on the domain or not. workgroup matches up im looking over my smb.conf for the 100th time everything appears fine?

---

### Post by Phurious on 2007-11-12
You may be beyond this, but this helped me.

[http://www.youtube.com/watch?v=Ad17kma8rNM]("http://www.youtube.com/watch?v=Ad17kma8rNM")

---


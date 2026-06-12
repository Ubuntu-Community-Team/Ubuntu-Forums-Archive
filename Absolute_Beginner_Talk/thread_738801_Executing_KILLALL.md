---
title: "Executing KILLALL?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by astrosoft on 2008-03-29
Hi guys!

I'm trying to execute 
              sudo -u www-data killall -v pppd
and it doesn't work!

When i enter sudo -u root killall -v pppd ,
everything works fine.
I have also put www-data (ALL) ALL into sudo visudo,
but i didn't get any result.

Can anyone help me?
It's really a big thing for me, because I NEED to run this script via PHP.

Thx...

---

### Post by Oldsoldier2003 on 2008-03-29
> **astrosoft said:**
> Hi guys!

I'm trying to execute 
              sudo -u www-data killall -v pppd
and it doesn't work!

When i enter sudo -u root killall -v pppd ,
everything works fine.
I have also put www-data (ALL) ALL into sudo visudo,
but i didn't get any result.

Can anyone help me?
It's really a big thing for me, because I NEED to run this script via PHP.

Thx...
just a thought... if you were able to get this working it would probably introduce a huge security hole into your apache installation...

---

### Post by astrosoft on 2008-03-29
I don't really care 'bout that - the server running ubuntu doesn't have any personal data anyway. I just want it working.

---

### Post by astrosoft on 2008-03-29
I can't believe no one knows anything about this!!!

---

### Post by edward4130 on 2008-03-29
instead of sudo have you just logged in as root and ran it?
```
su -l root
```
that may get you around it unless you disabled root, and for a home or small biz that would be crazy.

Edward4130

---

### Post by Whiffle on 2008-03-29
how about sudo killlall -u www-data -v pppd

---

### Post by Dr Small on 2008-03-29
It seems like you have 2 threads running on this:
[http://ubuntuforums.org/showthread.php?t=738823](http://ubuntuforums.org/showthread.php?t=738823)

---


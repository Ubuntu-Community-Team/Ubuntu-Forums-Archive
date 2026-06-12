---
title: "ipmasqing"
date: 2007-01-08
forum: Apple PPC Users
---

### Post by wanger123 on 2007-01-08
Hi, I don't want to post in 2 forums, but I want to know how to run etc/init.d/ipmasq restart without a password and automatically at login? (see my post in networking section)

thanks

wanger

---

### Post by calum on 2007-01-09
> **wanger123 said:**
> Hi, I don't want to post in 2 forums, but I want to know how to run etc/init.d/ipmasq restart without a password and automatically at login? (see my post in networking section)

thanks

wanger

I'd guess you'd want to add /etc/init.d/ipmasq to your sudoers file (using visudo), to get around the password request.  Then you'll want to run 'sudo /etc/init.d/ipmasq restart' somewhere appropriate (e.g. your ~/.bashrc file if you always have  a terminal running in your session like I do, or maybe investigate GNOME's 'things to run at login time' options in the Session preferences dialog).

---


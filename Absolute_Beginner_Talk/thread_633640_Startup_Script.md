---
title: "Startup Script"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by brotherajnin on 2007-12-06
I believe this is a simple startup script issue, but please correct me if I'm wrong.  I recently installed Maple on my computer, and to run it, I need to type " /home/ajnin/maple11/bin/maple".  Is there a way for me to only type "maple"?

Similarly, before I use my VPN software, I need to type "sudo /etc/init.d/vpnclient_init start".  How do I run this automatically at boot?  

Thanks a lot!!

---

### Post by TheWizzard on 2007-12-07
> **brotherajnin said:**
> I believe this is a simple startup script issue, but please correct me if I'm wrong.  I recently installed Maple on my computer, and to run it, I need to type " /home/ajnin/maple11/bin/maple".  Is there a way for me to only type "maple"?

Similarly, before I use my VPN software, I need to type "sudo /etc/init.d/vpnclient_init start".  How do I run this automatically at boot?  

Thanks a lot!!


you shouldn't put software in your user dir, but in /usr/local
then you can use path 
[http://www.faqs.org/docs/Linux-mini/Path.html](http://www.faqs.org/docs/Linux-mini/Path.html)



```
sudo nano -B /etc/rc.local
```
then add: /etc/init.d/vpnclient_init start

---


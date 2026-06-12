---
title: "HAL error"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by bhavesh on 2006-12-11
When i restarted ubuntu 6.10 i got the error "failed to initialize HAL"

What does this error mean ?

Thanks , 
Bhavesh

---

### Post by Iowan on 2006-12-11
[http://ubuntuforums.org/showthread.php?t=297975]("http://ubuntuforums.org/showthread.php?t=297975")
I found several links by clicking on the [hal]("http://ubuntuforums.org/tags/index.php/hal/") tag you used.
This one just happened to have:
> HAL is an acronym (Hardware abstraction layer)

---

### Post by Len_C on 2006-12-12
I had the same problem. I fixed it by
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12

---

### Post by TheRingmaster on 2006-12-12
> **Len_C said:**
> I had the same problem. I fixed it by
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12
what does that command do?

---

### Post by Len_C on 2006-12-13
Have a look at [https://launchpad.net/distros/ubuntu/+source/dbus/+bug/19577](https://launchpad.net/distros/ubuntu/+source/dbus/+bug/19577)

---


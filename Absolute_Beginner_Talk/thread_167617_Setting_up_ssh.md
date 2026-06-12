---
title: "Setting up ssh"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by zappadragon on 2006-04-28
OK so I have my Ubuntu box setup and I want to be able to ssh from my Windows pc to my Ubuntu box. I have Putty installed on my Windows box but what do I need to do on the Ubuntu box? I try with putty to ssh ipaddress and it says access denied. I am not able to even try and login.

Please help!

I hope I gave enough info for everyone

---

### Post by mentallysilent on 2006-04-28
you need openssh-server on your server machine....fire up synaptics and install it...you can then use update-rc.d so to have it loaded when you boot....
also take a look here:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-openssh-server-config.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-openssh-server-config.html)

---

### Post by zappadragon on 2006-04-29
Thanks much for the help! worked get and was exactly what i have been trying to do.

thanks again

---


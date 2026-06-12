---
title: "VmServer and Windows Xp, need help"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-03-24
Ok after following some advice on how to fix my Vmserver I inserted this code.

```
cd /etc/vmware
sudo mv not_configured not_configured.bkup
``` 

I was under the impression this would make it so I would no longer have to config the server every time  I wanted to run WindowsXp. So now I can start the server up but I no longer have access to Internet and I receive the following errors.

[IMG]http://i13.tinypic.com/3zbwzsn.png[/IMG]

But the strange thing is now, the only way to run the server is to enter the code above every time I restart my PC, if I try to start the server using the Terminal I get this error.

[IMG]http://i12.tinypic.com/2u7qa09.png[/IMG] 

Can someone please help me.
Thanks

---

### Post by aktiwers on 2007-03-24
Did you try to do as it says? 
Run :
```
sudo /usr/bin/vmware-config.pl
```

have you done that yet?

---

### Post by Repent on 2007-03-24
Yes it shows that I did in the bottom image.

Thanks for the reply.

---

### Post by khedron on 2007-03-24
It seems that the problem is with stopping one of the VMWare services. 
Maybe you could try booting into recovery mode so that the service never gets started in the first place, then running vmware-config.pl from the recovery console.

You are root when you go into recovery mode, no need to prefix everything with sudo.

---


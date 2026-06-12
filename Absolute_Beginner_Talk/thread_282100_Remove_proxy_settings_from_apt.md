---
title: "Remove proxy settings from apt?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by phantasmagoriana on 2006-10-22
Hi,

I've recently moved from an network connection that was behind a proxy to one that isn't. I've removed the proxy settings from Firefox, Synaptic and the system network proxy configuration, which is all working. However, I don't know how to stop apt from trying to use the proxy. If I run printenv it shows that a proxy is configured, but I don't know what to edit? 

Any suggestions would be much appreciated.

---

### Post by Najand on 2006-10-22
Try to edit your /etc/apt/apt.conf
and change it to:
```

Acquire::http::Proxy "false";

```

---

### Post by phantasmagoriana on 2006-10-22
Thanks for the suggestion - tried it but didn't seem to make any difference, I'm still getting a 407 error message and it's trying to find the nonexistent proxy...

---

### Post by phantasmagoriana on 2006-10-22
Can anyone suggest anything else I can try for this? Not being able to run apt-get is getting quite frustrating...](*,) 

Thanks

---

### Post by moufranica on 2006-11-25
We ran into the same problem you are running into. apt-get insist on using a proxy server. Hence we installed a local proxy, and change the http_proxy environment to this local proxy whenever we want to do an update. A bit tedious, but it works. Try it.

---


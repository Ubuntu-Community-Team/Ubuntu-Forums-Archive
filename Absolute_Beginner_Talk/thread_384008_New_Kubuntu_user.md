---
title: "New Kubuntu user"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by jhrisley on 2007-03-13
Son has just gotten Kubuntu OS and I would like to know if there is any decent internet filters available for this operating system that are based on an outside server (tamper proof).  Thanks.

---

### Post by orkim on 2007-03-14
There are a number of proxy services that will offer content filtering.  However, these depend on setting the proxy settings on the browser.

Your most effective way of providing content filtering would be to remove root privileges from him (i.e. only you know the password) and then close all incoming/outgoing ports.  You could then set up a proxy (say port 8080 or similar) and then only allow in/out bound communications from the proxy.  This proxy can do all the filtering/logging that you would like.

One note: you would also need to revoke the sudo privileges that the first user will get my default.

There are two options anyways.  I hope this might have given you an idea of how to accomplish you goals at least.  Neither of them are for the beginner (which I am going to assume that you are because of posting in this forum).  The second one especially is advanced way to accomplish content filtering.

Hope that helps!

-orkim

---


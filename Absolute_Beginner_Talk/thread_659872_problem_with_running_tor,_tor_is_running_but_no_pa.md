---
title: "problem with running tor, tor is running but no page opens"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-06
Hi, Thank you for reading my post.
I have installed TOR using **sudo apt-get  install tor**
I also installed tor button in order to have easy switch between plain network use and proxied use.

but now when I try to access any web page it show the error : the page can not be displayed.

What can I do?
I tried to run tor using console and it returns:

```

Jan 06 15:10:58.034 [notice] Tor v0.1.2.17. This is experimental software. Do not rely on it for strong anonymity.
Jan 06 15:10:58.035 [notice] Initialized libevent version 1.3b using method epoll. Good.
Jan 06 15:10:58.035 [notice] Opening Socks listener on 127.0.0.1:9050
Jan 06 15:10:58.035 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jan 06 15:10:58.036 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Jan 06 15:10:58.036 [err] Reading config failed--see warnings above.

```


I am using Ubuntu 7.10 32 bit edition.

How can i find whether the ISP filtered tor? I can access tor official site but i do not know whether it means that tor is not filtered by my isp or not.




Thank you

---

### Post by hopelessone on 2008-01-06
did you follow this guide...

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

worked for me...

---


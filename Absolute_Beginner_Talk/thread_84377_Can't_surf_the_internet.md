---
title: "Can't surf the internet"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by jamsession on 2005-10-30
I am running brezzy 5.10 and can't pull any websites up.

I went into the about:config and turned the network,dns.disableipv6 to true, but still nothing?

I have read through alot of post w/ the same problem but it didn't help.
 I did the ....
```

sudo gedit /etc/modprobe.d/aliases
```

but nothing came up but crap at the bottom of the termanal like ^R Read ^T write etc.

When i do the "ifconfig" everything seems to be in place???

---

### Post by Qrk on 2005-10-30
type 

sudo dhclient 

into a terminal, and post the output. (I might know how to fix it, and it will help anyone that does)

---

### Post by darth_vector on 2005-10-31
try:

ping 66.102.7.99

this is a google web server. if you cant ping it you are not connected to the net (if this is so, how are you trying to connecting to the net? are you using a gateway?). if you can ping it try

ping [www.google.com](www.google.com)

if you cant ping it you have a DNS issue. add some dsn servers to /etc/resolv.conf, if you can ping it then you probably just have an issue with your browser.

---


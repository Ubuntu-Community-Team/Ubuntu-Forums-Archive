---
title: "Unable to view websites"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by OMJD on 2006-03-02
For some reason I'm unable to view websites on my Ubuntu system. I am able to ping google fine without any problems. But can't get any website or gaim to work.

This also happened a few hours ago when I was using Fedora Core 4. It doesn't happen when using Windows XP on that machine though.

Any ideas?

Thanks. :)

---

### Post by suRoot on 2006-03-02
```
telnet www.google.com 80
```

from a console, which should return something like

```

Trying 216.239.37.104...
Connected to www.l.google.com.
Escape character is '^]'.
```

If any device is between you & the internet (proxy / etc), it will respond in place of the web site.  That may help you figure out what's blocking the connection.  If you get the same response as above, your other apps should be working fine.

---

### Post by OMJD on 2006-03-02
Thanks for the response.

It just says:

> Trying 1.0.0.0...

---

### Post by suRoot on 2006-03-03
I think your problem is related to IPv6, so try disabling it...
```

sudo gedit /etc/modprobe.d/aliases
```

find the line that reads

```
alias net-pf-10 ipv6
```

and comment it out.

```
# alias net-pf-10 ipv6
```

also, add the following lines (I added mine below the existing entry which you just commented out)

```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
```

Reboot your box after making this change.

Check your firefox config, too, & disable IPv6

1. In Firefox, type about:config in the address bar and click Go.
2. Type ipv6 in the Filter box. This should show you the config option, "network.dns.disableIPv6".
3. Double-click network.dns.disableIPv6 to change it from false to true.

---

### Post by OMJD on 2006-03-03
Thanks for your help, I will try that.

One question though, just so I can understand better, what is IPv6 and what does it do?

Thanks. :)

---

### Post by suRoot on 2006-03-03
See this:
[http://searchvb.techtarget.com/sDefinition/0,290660,sid8_gci212389,00.html](http://searchvb.techtarget.com/sDefinition/0,290660,sid8_gci212389,00.html)

---

### Post by mikes34 on 2006-03-03
I had the same problem, also with FC 4... thanks for great advice... it works, really thank you very much

---

### Post by ndhilliprasad on 2008-03-12
I am also having the same problem with accessing this [http://addons.mozilla.org/firefox/addon/3911](http://addons.mozilla.org/firefox/addon/3911) 

I have disabled the ipv6 as mentioned in the above post, but no luck 

Please help me to solve the problem

when i do  telnet [www.addons.mozilla.org](www.addons.mozilla.org) 80 
result is:
telnet: could not resolve [www.addons.mozilla.org/80:](www.addons.mozilla.org/80:) Name or service not known

---


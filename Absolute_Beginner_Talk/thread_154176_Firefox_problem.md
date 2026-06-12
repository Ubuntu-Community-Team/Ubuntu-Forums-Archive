---
title: "Firefox problem"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by flabbas on 2006-04-02
I've got a fresh install of ubuntu 5.10, i've run all the updates etc etc, the machine is on my home network, it has grabbed an IP fine, can ping everything and can ping web pages all is hunky dory in that respect.

But when i try and bring in a web page through firefox it does nothing - I've checked the network configuration and all seems fine - is there something I'm missing?

Any help is appreciated

---

### Post by kent41 on 2006-04-02
[QUOTE=flabbas]I've got a fresh install of ubuntu 5.10, i've run all the updates etc etc, the machine is on my home network, it has grabbed an IP fine, can ping everything and can ping web pages all is hunky dory in that respect.

But when i try and bring in a web page through firefox it does nothing - I've checked the network configuration and all seems fine - is there something I'm missing?

Any help is appreciated[/QUOTE]

some routers and systems can't handle IPV6
You might try the following:

  ```

       sudo gedit /etc/modprobe.d/aliases 
 
      Find the line:  alias net-pf-10 ipv6 

      Replace it with:  alias net-pf-10 off 

      Save the file and restart your computer


```

---

### Post by rfruth on 2006-04-02
Firefox can't see the network how about some other browser and or e-mail program ?

---

### Post by flabbas on 2006-04-02
That solved it - thanks :)

---


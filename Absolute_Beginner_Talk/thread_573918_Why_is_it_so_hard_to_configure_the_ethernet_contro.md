---
title: "Why is it so hard to configure the ethernet controller?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-10-12
In Windows 2000 it is easy.  You click on the CONFIGURE button,
get to some tabs, click on ADVANCED and there is a window
with several options, including Media Type, which I needed to
change, and I get a nice little set of choices, including 10Base Tx,
which is what I need

So I go back to Edgy and where do I do this?  

Someone please help!!!

Thank you,
Michl

---

### Post by cowkiller on 2007-10-12
*System>Adminitration>Network* ?

---

### Post by Michl on 2007-10-12
System -> admin-> Network does not give you the option
to change duplexes, flow control, media types, and so
on.  It allows you to set the network addresses, dns and
so on, and not to configure the ethernet controller.

Sheesh

---

### Post by Michl on 2007-10-12
ethtools is the answer.  Runs in the terminal window.

---

### Post by hyper_ch on 2007-10-12
Manual Page:
```

man interfaces

```

Editing:
```

sudo nano /etc/network/interfaces

```

---

### Post by Michl on 2007-10-12
It seems tha I have to run ethtool everytime I boot-up.  I looked at
the interface file before without much luck but maybe this time after
playing with ethtool it will lmake more sense..

well, now it isn't working again in ubuntu.  back to windows to
connect to the internet.  One thing is in ubuntu i'm told that
checksum isn't supported but in windows it is enabled.

I'm sure there is a solution, but /etc/network/interface
and ethtool are pretty difficult to use compared to ms,
I hate to admit.

---


---
title: "[SOLVED] ubuntu host xcfe message"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by jjbro on 2008-03-22
I just installed Xubuntu the other day - went fairly well.

However, when starting up the computer I get the following message:

"could not find internet address for ubuntu". This will prevent Xfce from running normally. Add ubuntu to /etc/hosts"

I have not noticed any malfunctioning of Xfce? So I cannot figure out, what this means - and what to do?

Please help.:)

---

### Post by jjbro on 2008-03-23
Found out myself.

When configuring the network, the installation somehow missed to setup my computer = host = ubuntu against the ip-adress 127.0.0.1.

I went into the network configuration tool and corrected this under "hosts".

I did not see any effects of this omission - apart from the error message when starting up xubuntu.

---


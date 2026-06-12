---
title: "Poor Connection on University Campus"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by xItachi on 2008-02-21
Hi, my laptop successfully connects to the university network and I login to get access to the internet.  However, after 5 minutes or so, the connection is lost, but it still says I'm connected to the university network.  I refresh the page but it doesn't successfully load.  It doesn't even load the page to login to the network.  The disconnects are very frequent and I  often have to wait long periods in order to try it again.  Does anyone know what's wrong?  Thanks.

---

### Post by cowboysurfer on 2008-02-21
Is your laptop new? Or was it running a different OS before? I know at my university in order to use the wireless internet we have to register the IP of the device we want to use online either at another computer or online some other time. Otherwise it will show a signal but does nothing as far as connecting to the network is concerned.

---

### Post by spiderbatdad on 2008-02-21
you might try disabling ipv6 routing by editing /etc/modprobe.d/aliases to look like this :
```
gksu gedit /etc/modprobe.d/aliases
```

```
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
**alias ipv6 off**
**alias net-pf-10 ipv6 off**
alias net-pf-11 rose
alias net-pf-12 decnet
``` Save the file.

---

### Post by macogw on 2008-02-22
Do you have a Broadcom card?  I've had the same trouble with the Broadcom card in the laptop I borrowed from my roommate.  My laptop's Intel card works perfectly under Ubuntu/Linux.

---

### Post by bumanie on 2008-02-22
I answered a similar post a week or two back. For the user, blacklisting ipv6 worked. Either use superbatdad's suggestion or else 
> sudo gedit etc/modprobe.d/blacklist
at the bottom of the list type 
blacklist ipv6
Save and reboot.
You can always reverse this if it doesn't help.

---

### Post by xItachi on 2008-02-22
cowboysurfer, my laptop is not new.  It was running Windows before and I have registered the IP of this laptop for wireless use on campus.  Do I have to register it again now that I'm dualbooting Ubuntu?

---

### Post by xItachi on 2008-02-28
I tried spiderbatdad and bumanie's solution and for the most part I think it gave me better connection on campus, but I'm not sure if the problem is completely resolved yet.

---


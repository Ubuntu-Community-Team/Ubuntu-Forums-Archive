---
title: "windows network"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Nectovelius on 2007-10-16
How do I acces my shared windows drive from Ubuntu? I went under windows network and there is nothing there... Please be specific in your instructions as I just installed ubuntu and I am not yet familiar with linux.
Thanks

---

### Post by callan79 on 2007-10-16
> **Nectovelius said:**
> How do I acces my shared windows drive from Ubuntu? I went under windows network and there is nothing there... Please be specific in your instructions as I just installed ubuntu and I am not yet familiar with linux.

Hello,

Due to whatever reasons (firewalls, windows not playing nice, who knows!), I have found that the 'browse network' type functions in both Windows AND Ubuntu can be a little unreliable.

You'll find that each computer on your network has an IP Address, for example my computer is 192.168.7.21, yours might be similar. Each computer on the network has a unique IP Address.

To find out your IP Address in Ubuntu, do this at terminal :
```
ifconfig
```

In Windows, do this at your command prompt (start >> run >> cmd [enter])
```
ipconfig
```

Then to access your Windows shares from Ubuntu, go to places >> computer. At the top there is a little bar that tells you the previous folders you have looked at. There is a button on the left that changes this to an address bar you can type in. Delete everything in the bar and type this :
```
smb://192.168.7.21
```

But of course you need to type whatever the IP Address is of your Windows computer.

Let us know how you go!

Cheers
Callan

---

### Post by skrimpy on 2007-10-17
Your solution helped me Callan, thanks!

---

### Post by Nectovelius on 2007-10-18
works pretty well thanks!:guitar:

---


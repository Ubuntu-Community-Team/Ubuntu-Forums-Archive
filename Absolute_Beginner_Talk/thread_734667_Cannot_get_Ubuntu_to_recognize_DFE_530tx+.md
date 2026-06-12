---
title: "Cannot get Ubuntu to recognize DFE 530tx+"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by HamiltonJR on 2008-03-24
Hello! I just installed Ubuntu on an old HP Pavillion. The install went fine and the O/S boots, but I cannot connect to the internet b/c my network card (DFE 530tx+) is not recognized.

I saw in another forum to run lspci. This returns information about Intel 82850, Intel 82801 (I think) and GeForce.

Can someone help me figure out why my network card is not recognized? I currently have Ubuntu running from the live CD (i.e. I rebooted the Pavillion with the CD in the reader) and the network admin only shows one entry for "modem"

Any help would be GREATLY appreciated.

John Hamilton

---

### Post by coolbrook on 2008-03-24
Does the adapter light up when you boot your system or show up as a listed device during POST?

What is the output of terminal command

```

ifconfig
```

---

### Post by kolisikepu on 2008-03-25
What model HP Pavillion you using?

---

### Post by HamiltonJR on 2008-03-25
Pavillion 9800

---

### Post by HamiltonJR on 2008-03-25
The adapter light does light up; the activity light shows no signs of life...

ifconfig (running on my Ubuntu machine, so cannot cut/paste)...
lo          Link endcap: Local loopback
            inet addr: 127.0.0.1  mask: 255.0.0.0
            inet6 addr:  ::1/128  Scope: Host
            UP LOOKBACK RUNNING  mtu:16436  METRIC: 1
            Then some stuff about Tx and Rx packets.

---

### Post by coolbrook on 2008-03-25
```
ifup eth0
ifup eth1
ifconfig
```

---

### Post by HamiltonJR on 2008-03-25
> **coolbrook said:**
> ```
ifup eth0
ifup eth1
ifconfig
```

ifup etho ... failed to open statefile /var/run/network/ifstate: Permission denied.

ifup eth1 ... failed to open statefile /var/run/network/ifstate: Permission denied.

ifconfig ... same as before.

---

### Post by HamiltonJR on 2008-03-25
> **HamiltonJR said:**
> ifup etho ... failed to open statefile /var/run/network/ifstate: Permission denied.

ifup eth1 ... failed to open statefile /var/run/network/ifstate: Permission denied.

ifconfig ... same as before.

Did an su to root...

ifup eth0 ...
eth0 error while getting interface flags: no such device

---

### Post by Mogurijin on 2008-03-25
Have you tried installing your Windows drivers for you adapter through ndiswrapper?

---

### Post by HamiltonJR on 2008-03-25
> **Mogurijin said:**
> Have you tried installing your Windows drivers for you adapter through ndiswrapper?

I do not know what that means?

---

### Post by Mogurijin on 2008-03-25
Alright, there is a wrapper called ndiswrapper that allows you to use windows wireless drivers in Linux. I've had pretty good success with this using Netgear adapters. You can install ndiswrapper off the cd (since you obviously aren't connected to the internet with that machine). Check Administration -> Software Sources and the CD should be there. Then you can just use apt-get install ndiswrapper. Search the forum for the name of the troublesome adapter, you might find a How-to.

---

### Post by HamiltonJR on 2008-03-25
The adapter that I have in my PC is a wired adapter, not a wireless one. Is ndiswrapper still the way to go?

---


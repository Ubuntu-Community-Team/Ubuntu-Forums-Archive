---
title: "Can't get ethernet to work"
date: 2008-02-05
forum: Apple PPC Users
---

### Post by whm on 2008-02-05
I am completely new to linux, only OSes I have experience with are Mac and Windows and some BASIC way back in college. LOL

I am running the Kubuntu 6.06.1 LTS (Dapper Drake) on a B&W G3.  I have not yet installed, just running from the CD, I am waiting on a  new hard drive I ordered to install to.  

I can not get Kubuntu to connect to the internet using the ethernet cord that is plugged into my router.  The router assigns the DHCP id.  The internet works fine on Mac OS 10.2.8 and also if I boot from the Ubuntu 6.06 CD.  I can always use the Ubuntu, but I like the look of Kubuntu better.

Is there something I have not seen in the forums that can tell me how to get the internet to work on Kubuntu?  Is the problem from running from the CD?

Thanks for any help.

Harrison

---

### Post by ruy_lopez on 2008-02-05
What's the output from running:

```
ifconfig
```

---

### Post by whm on 2008-02-05
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:78980 (77.1 KiB)  TX bytes:78980 (77.1 KiB)




Thanks for any help.

---

### Post by ruy_lopez on 2008-02-05
> 
Re: Can't get ethernet to work
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1015 errors:0 dropped:0 overruns:0 frame:0
TX packets:1015 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:78980 (77.1 KiB) TX bytes:78980 (77.1 KiB)

There's your problem. 

lo is the loopback interface. The livecd hasn't recognised your interface. This doesn't necessarily mean that ubuntu doesn't support it. It only means the livecd hasn't detected it.

Do you know what kind of ethernet interface it is?

The livecd doesn't always detect interfaces. But you should check the interface is supported before going ahead with a full install.

That said, if you are feeling brave, you might install Ubuntu and hope for the best. I've never had a problem with PowerPC macs having their ethernet cards being detected on a full install.

---

### Post by whm on 2008-02-05
I am not sure of the interface, it is whatever shipped in the box.  One question.  The Unbutu CD does recognize the ethernet just fine, it is the Kubuntu CD that does not see it.  From your experience and knowledge would you hazard a guess that this is just a result of running from the CD?  

How do I check the type of card I have?

Thanks for all of you help, I am sure what I am asking is beyond basic.

---

### Post by ruy_lopez on 2008-02-05
I'm not familiar with Kubuntu. Someone else might be able to help. Is there a network config GUI with Kubuntu? Does it see the interface?

If you can see the name of the interface in the GUI (for instance "eth0" or something), then you can try this:

```
sudo ifup eth0 (or whatever eth* shows up in the GUI).
``` 

If it works with the Ubuntu LiveCD, I can only scratch my head why Kubuntu doesn't recognise it.

Check the network GUI configs for Kubuntu. That's all I can guess. Best of luck.

---

### Post by Dennis on 2008-02-05
What output does: ```
lspci -v
``` in the terminal give?
Scan down the output for Ethernet controller

---


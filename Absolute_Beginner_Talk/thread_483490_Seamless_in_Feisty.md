---
title: "Seamless in Feisty?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-24
Is there a way to run seamless in Feisty using VirtualBox? All the guides I have read are very complicated and don't appear to play nice with the Network Manager (wireless), or are meant for other programs... 

So, my question, is has anyone gotten this to work with a scenario close to mine? If so, could you please post/link a good tutorial telling me how to do this? 

Please let me know...
ts51

---

### Post by Jimmyfj on 2007-06-24
Not sure if this will help you out:

[http://www.google.dk/search?hl=da&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=seamless+in+Feisty+using+Virtual+Box&spell=1](http://www.google.dk/search?hl=da&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=seamless+in+Feisty+using+Virtual+Box&spell=1)

---

### Post by ts51 on 2007-06-24
[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359) 

Would this work in Feisty? 

Also, I noticed this: 

>  But I HAVE to use Network Manager, my <insert wireless card here> is only supported by it!” Then my friend, I apologize but you may be SOLIf I used WiFi radar, then would it work? 

Also this: 

> First, I have only tested this setup on a desktop with a physical, wired network connection. It may work wirelessly, but I have not tested it.Has anyone tested it? 

-ts51


All quotes in this post were from [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

---

### Post by ts51 on 2007-06-24
any ideas?

---

### Post by ts51 on 2007-06-25
?

---

### Post by T0MA on 2007-06-29
I got it working on Feisty with a wireless card and NAT connection. You don't have to mess with the host-only and kill network manager, simply port-forward a connection to the vm by applying these settings:

VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/Protocol" TCP
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/GuestPort" 3389
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/HostPort" 6666

You will be able to connect with rdesktop to the vm at localhost:6666

I have internet on both the host and the vm and seamless work 100%!

---

### Post by tekwiki on 2007-09-08
Thank you so much T0MA!!!!!

Doing the bridge method was killing internet connection and not functioning properly all around, doing the setextradata method works flawlessly!

Thanks!!!!


:guitar:

---


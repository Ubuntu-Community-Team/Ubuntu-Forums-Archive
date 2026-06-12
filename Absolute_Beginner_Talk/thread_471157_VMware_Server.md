---
title: "VMware Server"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by simon87 on 2007-06-11
I am trying to install and use VMware server 1.0.3 on ubuntu 7.04 but cannot get any of my created virtual machines to power on. 

I installed using synaptic and I can run the server console and create VM's but they will not power on. When I press power on it tries for a few seconds but fails giving no error message

What should I do?

Thanks
Simon

---

### Post by useResa on 2007-06-12
Have you tried starting the vmware server from the terminal?
Open a terminal (Applications --> Accessories --> Terminal) and issue the command
```
vmware
```
This may give additional information on why the server is not starting.

Furthermore, AFAIK, there are log files created when you start your vmware server.
Maybe these files can give you some info (directory /var/log/vmware).

---

### Post by huygens on 2007-06-12
> **simon87 said:**
> I am trying to install and use VMware server 1.0.3 on ubuntu 7.04

How did you install it?
The [VMware Server 1.0.3 is available in the commercial repository of Ubuntu]("http://www.berthon.eu/ice_and_fire/?p=70"), did you use that installation or did you install it manually?
Are you running the 32 or 64 bit version of Ubuntu?

---

### Post by eentonig on 2007-06-13
I'm having the same issue. Installed from the repo's.

I doublechecked my file permissions and even started vmware as root.  
Starting up from the console doesn't give much info

> rfonteyn@gauloises:/var/lib/vmware-server/Virtual Machines$ vmware
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)


---

### Post by useResa on 2007-06-13
> **eentonig said:**
> I'm having the same issue. Installed from the repo's.

I doublechecked my file permissions and even started vmware as root.  
Starting up from the console doesn't give much info

I resolved this issue by issuing the following commands (one at a time):```

[FONT=Tahoma]cd /usr/lib/vmware/lib/
sudo mv libpng12.so.0/libpng12.so.0 libpng12.so.0/libpng12.so.0.disabled
sudo ln -sf /usr/lib/libpng12.so.0 libpng12.so.0/libpng12.so.0
sudo mv libgcc_s.so.1/libgcc_s.so.1 libgcc_s.so.1/libgcc_s.so.1.disabled
sudo ln -sf /lib/libgcc_s.so.1 libgcc_s.so.1/libgcc_s.so.1[/FONT]
```

Hope this helps you too.

---


---
title: "wired network connection - how to make it alive?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-07-02
Hello,

I just connected my notebook to a network cable. I know that this cable works, but on my lap with ubuntu, it says that connection is established, but in fact nothing works ("server not found" notification) and I cannot view connection information: "couldn't find some required resources (the glad file)"

I didn"t enter any subnet mask or other numbers, should I enter them somewhere?

---

### Post by Bachstelze on 2007-07-02
Network running DHCP ? If so, all you need to do is

```
sudo dhclient ethX
```

(with the correct name of your interface, of course)

---

### Post by Computer-Geek on 2007-07-02
If server has linux read step 2 and skip step 3 or if server has windows skip step 2 and read step 3.

1.Give the IP of server as Default Gateway of linux.  
2.Enable Internet Connection Sharing(ICS) through firestarter (but still u got to perform first step); Step for Linux server
3.Goto properties of internet connection; Step for Windows server
4.Goto advanced tab.
5.Enable the "Allow other computer to connect through this connection" option.
NOTE: The option stated in step 5 may be a little bit different, so dont panic u just have to enable ICS.

---

### Post by O-pos on 2007-07-02
I did that code in terminal, but I get error messages:

ethX: ERROR while getting interface flags: no such device
ethX: ERROR while getting interface flags: no such device
Bind socket to interface: No such device

---

### Post by ushills on 2007-07-02
You need to substitute ethX with the actual ethernet port being used, likely to be eth0 or eth1.

---

### Post by Ayuthia on 2007-07-02
What HymnToLife is saying is to replace the X in ethX with a number such as 0 or 1.  If you type ifconfig at the terminal, it will list what you have.  If you are not sure which to use, just post the results of ifconfig.

---

### Post by nitro_n2o on 2007-07-02
There should be no problems with your connection 

First check /etc/network/interfaces 
and make sure that you see these lines 
```
auto eth0 
iface eth0 inet dhcp
```
and check your browser! it might be configured to use some proxy server. 
As the guys said post your ifconfig eth0 commmand

---


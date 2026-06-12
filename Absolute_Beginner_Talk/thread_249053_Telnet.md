---
title: "Telnet"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by nichols430 on 2006-09-02
I need help configuring Telnet for my machine, I dont care about the SSH or whatever it is.. I just want Telnet , I have a local network, no internet to it, I just want it working so I dont have to use a KVM or another application installed onto my desktop.

Thanks,

Ryan

---

### Post by deanlinkous on 2006-09-02
Well you would need a telnet server running on whatever machine you want to connect TO and then use a telnet client on the mchine you want to telnet FROM.

What exactly are you wanting to do?

---

### Post by nichols430 on 2006-09-02
trying to leave the box under the table and not have a KVM connected to it so I can still use the Samba on it.  I have telnet installed, I did the apt-get thing and it said it was installed, its not accepting my connection from the windows enviroment, I know its on the network because Samba's working.

It says : Could not open connection to host, on port 23.  Connection failed.

---

### Post by xhaan on 2006-09-02
If you downloaded "telnet", you only have the telnet client.
You need telnetd, (yes thats "telnet" with a d at the end.) which is the telnet server... I'm not sure if it's in the repositories or not, I couldn't find it, or any other telnet server for that matter.

Just thought I'd let you know about this, I'd help you get telnetd but I'm new to Ubuntu myself and find that its missing a couple things that I'm normaly used to having..

---


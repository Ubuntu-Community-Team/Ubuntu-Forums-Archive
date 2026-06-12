---
title: "Firestarter block everything"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-02-23
Hello all
I am using firestarter. I have not changed its default settings and set it to work with Local Area Network (LAN). But what I use it, I cannot access any smb network resources and/or win32 file sharing servers. Can anybody help me with the configuration?

---

### Post by mrsteveman1 on 2008-02-23
If the firewall is setup as a default deny for incoming stuff it should still allow outgoing connections to anything.

Attach/post the output of sudo iptables -L so we can see what rules are loaded into netfilter

---

### Post by sayakb on 2008-02-23
glade@Muzic-Jukebox:~$ sudo iptables -L
Scan right index finger on AuthenTec AES2501
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
glade@Muzic-Jukebox:~$

---

### Post by TheWizzard on 2008-02-23
> **LinuxIsInnovation said:**
> Hello all
I am using firestarter. I have not changed its default settings and set it to work with Local Area Network (LAN). But what I use it, I cannot access any smb network resources and/or win32 file sharing servers. Can anybody help me with the configuration?

what do you mean with "set it to work with LAN"? please explain.

in order to add smb policies do the following: 
if the smb client has static ip, just allow the port samba uses from that ip



why did you install firestarter in the first place???

---

### Post by mrsteveman1 on 2008-02-23
If thats what iptables returned it isnt blocking anything at all, its accepting all packets and allowing all outgoing packets.

Is firestarter running right now?

---

### Post by sayakb on 2008-02-23
> **mrsteveman1 said:**
> If thats what iptables returned it isnt blocking anything at all, its accepting all packets and allowing all outgoing packets.

Is firestarter running right now?

Yes, firestarter is running right now. 
Let me elucidate: We have different IP addresses for different hostels in our college.. I am in Hostel-3, so my IP is of type 192.168.13.***. Similarly for H-4, it would be 192.168.14.***
Since there are more than 200 PCs in my hostel, it is impossible to add each PCs IP address. 
Here is a screenshot of firestarter's Events page:
[http://i32.tinypic.com/bhkart.jpg](http://i32.tinypic.com/bhkart.jpg)

It blocks all smb connections.

Also, I installed firestarter to configure my firewall to protect my computer from sending data to Win Packet Capture apps on the network.

---

### Post by TheWizzard on 2008-02-23
ok, just add a rule to allow smb. 
i think yoy can do this by right clicking one of the smb events.

---

### Post by sayakb on 2008-02-23
I have 5 options:

Allow connections from source
Allow inbound services for everyone
Allow inbound services for source
Disable events from source
Disable events on port

None seem to disable that service (I trried all, but they seem to have no effect)

---

### Post by TheWizzard on 2008-02-23
Allow inbound services for everyone should do the trick. klick apply and then try to make a new smb connection.

---

### Post by sayakb on 2008-02-23
By the way, If I allow smb, DHCP and UDP (UDP is used by IPMSG32.EXE a windows file sharing app used in our college, UDP @ Port 2425) then will the Packet Capture apps be able to access my computer?

---

### Post by sayakb on 2008-02-23
By the way, If I allow smb, DHCP and UDP (UDP is used by IPMSG32.EXE a windows file sharing app used in our college, UDP @ Port 2425) then will the Packet Capture apps be able to access my computer?? I want to block those apps..

---

### Post by mrsteveman1 on 2008-02-23
What are the packet capture apps your referring to?

You should be able to block anything you want to from firestarter.

---

### Post by sayakb on 2008-02-23
> **mrsteveman1 said:**
> What are the packet capture apps your referring to?

You should be able to block anything you want to from firestarter.

Packet capturing apps capture all password info sent from/recieved by my PC. I will not give any example since it may go against the forum rules :(

---

### Post by mrsteveman1 on 2008-02-23
Ok so you want to block specific machines on the network? Or specific ports?

---

### Post by sayakb on 2008-02-24
> **mrsteveman1 said:**
> Ok so you want to block specific machines on the network? Or specific ports?

Look what I did:

[http://i30.tinypic.com/4qsfog.jpg](http://i30.tinypic.com/4qsfog.jpg)

I added these to the policy rules:
The port 2425 is used by ipmsg32.exe as I said before. So with all these policies, can the backdoors and/or packet capture apps work. Also no, I dont want to block specific computers since there is no clue who is using those apps :(

---

### Post by sayakb on 2008-02-24
Thanks mrsteveman1 and TheWizzard. I added the rule to the policy list. Now I can access smb and use win32 file sharing apps.. Thank you again :)

---


---
title: "Unable to connet to internet"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by pavankumar25386 on 2007-12-09
Hi all, 
     Can any one help me to connect to internet??? I am able to connect to internet in WINDOWS but not in Ubuntu 7.10. When i am typing google.com or ubuntu.com in address bar it is displaying my sever page. i have some screen shots of this plz help me..

Thank you,

---

### Post by PointyWombat on 2007-12-10
Hi,

Could you please open a terminal and post the output for the following commands:

```
ifconfig eth0
```

```
netstat -r
```

```
ping -c 1 ubuntu.com
```

```
nslookup ubuntu.com
```

```
wget www.google.com
```

---

### Post by pavankumar25386 on 2007-12-10
Thanks for ur concern please be intouch till i connect tp internet
once again thank You.

---

### Post by bumanie on 2007-12-10
It may well be a problem with ipv6 which has plagued many 7.10 users. if the above does not work, the next thing to try would be to blacklist ipv6 - it was the only way I could the internet working in 7.10.
In terminal type
gksudo gedit /etc/modprobe.d/blacklist --> enter
at the end of the gedit list type (as in add onto the list)
blacklist ipv6. 
Save and reboot.
Your internet should work after reboot.

---

### Post by pavankumar25386 on 2007-12-10
**pavan@pavan:~$ ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr 00:19:21:80:1C:C3  
          inet addr:172.35.25.111  Bcast:172.35.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:21ff:fe80:1cc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:10 txqueuelen:1000 
          RX bytes:1124181 (1.0 MB)  TX bytes:5949 (5.8 KB)
          Interrupt:16 Base address:0xac00

**pavan@pavan:~$ netstat -r**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.35.0.0     255.255.0.0     U         0 0          0 eth0
link-local          255.255.0.0     U         0 0          0 eth0
default           172.35.0.1      0.0.0.0         UG        0 0          0 eth0
**pavan@pavan:~$ ping -c**
1 ubuntu.com
PING ubuntu.com (91.189.94.158) 56(84) bytes of data.

--- ubuntu.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

**pavan@pavan:~$ nslookup**
ubuntu.com
Server:         172.35.0.1
Address:        172.35.0.1#53

Non-authoritative answer:
Name:   ubuntu.com
Address: 91.189.94.158
**pavan@pavan:~$ nslookup ubuntu.com**
Server:         172.35.0.1
Address:        172.35.0.1#53

Non-authoritative answer:
Name:   ubuntu.com
Address: 91.189.94.158

---

### Post by PointyWombat on 2007-12-10
Hi, and thanks for the output. Can you post output for the wget command as requested above?

Also, in Firefox, is it configured for 'Direct connection to the internet' (Edit->Preferences->Advanced->Connection->Settings

Finally, when you put an ip in Firefox, instead of a name, does it work. Such as for google:

[http://72.14.253.147/](http://72.14.253.147/)



I'll also agree with BUMANIEs suggestion as a possible fix as I've seen IPV6 problems like this as well.

---

### Post by pavankumar25386 on 2007-12-10
Can you tell wat is the problem y i am unable to connect to internet??

---

### Post by pavankumar25386 on 2007-12-12
pavan@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:19:21:80:1C:C3  
          inet addr:172.35.25.1  Bcast:172.35.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:21ff:fe80:1cc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:60 txqueuelen:1000 
          RX bytes:3390882 (3.2 MB)  TX bytes:21087 (20.5 KB)
          Interrupt:16 Base address:0xac00 

pavan@ubuntu:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.35.0.0      *               255.255.0.0     U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         ubuntu.172.35.0 0.0.0.0         UG        0 0          0 eth0
pavan@ubuntu:~$ ping -c 1 ubuntu.com
PING ubuntu.com (91.189.94.158) 56(84) bytes of data.

--- ubuntu.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

pavan@ubuntu:~$ nslookup ubuntu.com
Server:         172.35.0.1
Address:        172.35.0.1#53

Non-authoritative answer:
Name:   ubuntu.com
Address: 91.189.94.158

pavan@ubuntu:~$ wget [www.google.com](www.google.com)
--20:03:40--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 64.233.189.104, 64.233.189.99
Connecting to www.google.com|64.233.189.104|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 231 [text/html]

100%[====================================>] 231           --.--K/s             

20:03:41 (12.54 MB/s) - `index.html' saved [231/231]

pavan@ubuntu:~$ wget [http://72.14.253.147/](http://72.14.253.147/)
--20:04:16--  [http://72.14.253.147/](http://72.14.253.147/)
           => `index.html.1'
Connecting to 72.14.253.147:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 231 [text/html]

100%[====================================>] 231           --.--K/s             

20:04:17 (12.48 MB/s) - `index.html.1' saved [231/231]

pavan@ubuntu:~$

---

### Post by PointyWombat on 2007-12-12
Hi Pavan,

Well, based on your posted output. It appears that your ineternet is OK. The only suggestion I have is to go ahead and disable IPV6 as per this link.

[OUTLINE: Disable IPv6]("http://ubuntuforums.org/showthread.php?t=6841")

Please let us know if you have success.

---

### Post by pavankumar25386 on 2007-12-12
Thanks and i willl try out and let u know wat is the result. 
Thanks again for your concern.

---

### Post by pavankumar25386 on 2007-12-13
One more thing is that i have any authentication check before connecting to internet.
means in windows we have to give correct UserID and Password in a application called 24 hours online provided by our ISP if user id and Password are correct we will be able to connect to internet.
Do you understand this ????
i will give u a screenshot.. of it.

---

### Post by pavankumar25386 on 2007-12-13
can this commands help me?? in connecting to internet

sudo pppoeconf
sudo ifconfig
sudo apt-getinstall pppoeconf
sudo pppoeconf
sudo pon dsl-provider
sudo ifconfig
sudo poff  (to close)

---

### Post by pavankumar25386 on 2007-12-13
I Got my Problem Solved by Following this.



      In the terminal type:



      sudo pppoeconf



   3.



      A text-based menu program will guide you through the next steps, which are:

         1.



            Confirm that your Ethernet card is detected.

         2.



            Enter your username.

         3.



            Enter your password.

         4.



            If you already have a PPPoE Connection configured, you will be asked if it may be modified.

         5.



            Popular options: you are asked if you want the noauth and defaultroute options and to remove nodetach - choose Yes.

         6.



            Use peer DNS - choose Yes.

         7.



            Limited MSS problem - choose Yes.

         8.



            When you are asked if you want to connect at start up, you will probably want to say yes.

         9.



            Finally you are asked if you want to establish the connection immediately.

---


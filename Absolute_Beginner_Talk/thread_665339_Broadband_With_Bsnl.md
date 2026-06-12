---
title: "Broadband With Bsnl"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by yvsmadhav on 2008-01-12
[SIZE="4"]I have a BSNL broadband and the modem is Huawei  SmartAX MT882 and it connects to the PC either via the ethernet port or through the USB.As I am experiencing problems with the ethernet port, I have switched over to the USB. THe modem connects whilst working with WindowsXP but when I log on to Ubuntu, I cannot connect to the internet. The modem driver cd contains drivers for Windows as well as for Linux. However, while I could install the relevant driver for Windows, I am unable to do the same when Ubuntu is concerned.May be because there is no .exe or setup file for Linux.[/SIZE]

---

### Post by esva on 2008-01-12
I know you can use .exe with wine,but I dunno if that works for drivers.
hmm
I know that for ubuntu the equal of .exe is .deb
maybe that will help you look for a solution, if you didn't know of it

---

### Post by kleo skywalker on 2008-01-12
Connect it to the ethernet port and try this:

Go to System-->Administration-->Network. Click on the "Properties" button next to "Wired Connection". Uncheck the "Enable roaming mode" box, set Configuration to "Static IP". Set the IP Address, Subnet Mask, Gateway Address. Back in the "Network Settings" menu, set DNS servers (primary and secondary). You will need to get these numbers from BSNL.

In the Terminal (Applications-->Accessories-->Terminal), run this command
```
sudo pppoeconf
```
Once done, reboot. You should be able to connect to the internet.

---

### Post by prashantryp on 2008-03-19
hello kleo skywalker

i have tried your way for mt882 but i received 

i got the error message

          Sorry, I scanned 1 interface, but the Access             &#9474;          
          Concentrator of your provider did not respond. Please              
          check your network and modem cables. Another reason                
          for the scan failure may also be another running pppoe             
          process which controls the modem.   

i am also unable to know whether my modem is installed or not when i put static ip and try to ping it it works but not with my modem/dns  ip it return error so do i know that system is communicating with my modem's ip. 

[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
:(

---

### Post by kleo skywalker on 2008-03-20
> **prashantryp said:**
> hello kleo skywalker

i have tried your way for mt882 but i received 

i got the error message

          Sorry, I scanned 1 interface, but the Access             &#9474;          
          Concentrator of your provider did not respond. Please              
          check your network and modem cables. Another reason                
          for the scan failure may also be another running pppoe             
          process which controls the modem.   

i am also unable to know whether my modem is installed or not when i put static ip and try to ping it it works but not with my modem/dns  ip it return error so do i know that system is communicating with my modem's ip. 

[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
:(

Don't worry about the error message, just let the process complete. Then reboot, and try to open web pages - it's the simplest way to find out if you are connected to the internet or not.
Just make sure you enter all the values mentioned in my previous posts in the right places. You may need to call your local internet service provider to ask for some of them, such as primary and secondary DNS servers.

---

### Post by prashantryp on 2008-03-21
hello kleo skywalker

THANKS FOR QUICK REPLY. :)

i was unable to connect to internet and received the message


 ifconfig -a

eth0      Link encap:Ethernet  HWaddr xx.xx.xx.xx.xx.xx
          inet addr:192.168.1.2  Bcast xxx.xxx.xxx.xxx  Mask:255.255.255.0
          inet6 addr: 				 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:623 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26935 (26.3 KB)  TX bytes:26935 (26.3 KB)

after running sudo pppoeconf i got the error message

          Sorry, I scanned 1 interface, but the Access                      
          Concentrator of your provider did not respond. Please              
          check your network and modem cables. Another reason                
          for the scan failure may also be another running pppoe             
          process which controls the modem.   

I like to make a WAN miniport pppoe connection LIKE IN WINDOWS so i can put user id and password to connect to my internet. I dont want autodial by modme's pppoe. 

I have seen my modem in ubuntu gutsy 7.10 device manager whith specification so i think it's installed.

Is it due to IPV6 because in windows it's woking with IPV4

THANK U

WAITING FOR YOUR ANSWER

---

### Post by kleo skywalker on 2008-03-21
I've never had to do anything beyond those steps to get my MTNL connection working, so I'm sorry I can't help further.
I keep reading about disabling IPV6 on the forums though, maybe you could try that?

---

### Post by nuke_fluke on 2008-04-29
> **kleo skywalker said:**
> Connect it to the ethernet port and try this:

Go to System-->Administration-->Network. Click on the "Properties" button next to "Wired Connection". Uncheck the "Enable roaming mode" box, set Configuration to "Static IP". Set the IP Address, Subnet Mask, Gateway Address. Back in the "Network Settings" menu, set DNS servers (primary and secondary). You will need to get these numbers from BSNL.

In the Terminal (Applications-->Accessories-->Terminal), run this command
```
sudo pppoeconf
```
Once done, reboot. You should be able to connect to the internet.

In the General column.
Host Settings: 
Host Name
Domain Name
What exactly does the above mean

---


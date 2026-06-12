---
title: "Multi-purpose server setup"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Baron Von Doolgas on 2008-02-24
Hello, I am setting up a server for multiple functions,  I am new to Linux and VERY rusty after 5 years away from computers all together.  My last computer I was using was an AMD K6-2 550mhz so it's been awhile!  After a little lingo refreshing and a few deals at Fry's I built a moderately powerful (as far as Ubuntu is concerned) server hoping it would hold-up to everyday use.

AMD BE-2300
ECS 7050M-M
2 GB -RAM
8500gt
3 NIC's - Onboard - 10/100
           - PCI - U.S Robotics -10/100/1000
           - PCIe - Intel -10/100/1000
ADD-ON PCI 5-port USB card
40gb hd single boot 

Hopes for the server
*As a server for a family website backed up by a pair of 320gb hd's in RAID 1
*Print server (I am really getting tired of switching around printer cables for wife)
*LAN server

I have a cable modem going into a Linksys router with a firewall feature. That is the internet router.  I am using my onboard as the LAN connection to a cheap Airlink router to  connect 4 downstream computers.   

This is my goal....have the Intel NIC as my 'website server only' 
                          The LAN computers will be able to access to internet using the US    Robotics NIC
                          LAN computers use printers connected to USB ports

I want to use the hardware firewall of the linksys and software firewall in UBUNTU to protect LAN computers, and a separate software firewall for my website server NIC.
Problem is, I don't know where to start.  I sit here reading about Apache, MySQL and Samba and I understand what they are, but not sure what I will need.  You don't need to tell me commands or anything, you could just be like..."hey stupid...start with this.." and so on.  Any help at all would be appreciated.  

Right now I have 7.10 installed with all hardware minus the intel NIC which is in mail.  Thank you - Doolgas

---

### Post by rapiscan on 2008-02-24
Apache is a webserver, which will allow you to serve the webpages.  You will definitely need a webserver of some sort (usually apache is recommended) if you want to serve webpages.

If Ubuntu server is installed, apache is already installed and likely already running.  Otherwise, you will want to start at this page:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

MySQL is a relational database.  Relational databases like MySQL are often used to store dynamic information for websites.  So if you want a website that collects and stores information from users (like posts in a forum, or user profiles) then you will want to use MySQL for this task.  Also, if you want to server dynamic webpages that are more than just HTML, you will want to use a scripting language like PHP.  Normal HTML only allows you to display static information, while PHP allows you to actually put program logic into your webpages.

You'll want to use Samba so that you can share files and print services on a windows network.  
You can start here:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
Once you get Samba up and running, this looks like a nice little page with information on sharing printers:
[http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html](http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html)

I'm not quite sure I understand your goal as the "LAN server" or the idea of separate firewalls, and I'm less familiar with these areas.  Hopefully someone else can offer some advice.

---

### Post by Baron Von Doolgas on 2008-02-24
Thanks for the help.

Basically what I mean when I say LAN server it's the host of my Local Area Network and it's used as the medium for file sharing, internet, etc.  Again, I am new to this as well so I am not sure if this is necessary.

---

### Post by rapiscan on 2008-02-24
Samba will allow your server to act as a file server.  

> I have a cable modem going into a Linksys router with a firewall feature. That is the internet router. I am using my onboard as the LAN connection to a cheap Airlink router to connect 4 downstream computers.


Unless I'm misunderstanding something, there's no need for your other computers to be connected to the internet through your ubuntu server.  This type proxy is commonly done if you want to filter information from the internet that is going to the other 4 computers.  It seems as though you should be fine connecting your 4 computers directly to the router, and perhaps installing a free software firewall on these computers. (Avast is a good choice, and it's free for non-business purposes).

Each of the computers will have their own IP address assigned by the router, and they will be able to communicate on the local network. The router does the job of routing incoming packets to the appropriate computer, so you don't have to do anything special in that regard.

---

### Post by Iowan on 2008-02-24
Check the howtoforge link in my sig - there are several good Ubuntu server how-to's there.

---


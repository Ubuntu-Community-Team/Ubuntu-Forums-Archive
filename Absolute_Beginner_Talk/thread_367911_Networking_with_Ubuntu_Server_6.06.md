---
title: "Networking with Ubuntu Server 6.06"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Stervyatnik on 2007-02-22
Hello, all! I'm re-doing my home network, and THIS TIME, I will learn how to do it if it kills me!

OK, I have installed Ubuntu Server 6.06 LAMP on a computer with 800Mhz, 20GB HD, 256MB RAM. I assigned it an IP Address of 192.168.0.0.

On three other computers, I installed Ubuntu Desktop 6.06, with IP Addresses of:

192.168.0.2
192.168.0.3
192.168.0.4

Because the Desktops have the graphical interface, I was able to configure each to "see" via ping the others by both IP Address and Host Name. But none of the workstations can ping the server. If I try to ping 192.168.0.0, the command line asks "Do you want to ping broadcast? then - b" - which mystifies me.

The server just uses the command line, so I'm flailing about a bit. I cannot ping the workstations from the server, despite having added IP Addresses and host names to the /etc/hosts file, using vi. I try to ping, and get "Host unreachable."

I have also attempted to restart the networking on the server, using "sudo /etc/init.d/networking restart," and it seems to go OK.

What am I doing wrong? Why can't the server ping the workstations, and vice-versa? Any help would be appreciated.

But I have learned a bunch! :)

---

### Post by keithweddell on 2007-02-22
I don't think you can use 192.168.0.0 as an IP address.  Try using 192.168.0.1 or 192.168.0.5 for the server.

Keith

---

### Post by Stervyatnik on 2007-02-22
That did it! Changed the IP Address for the server, and everybody's pinging everybody else.

Thanks!

---


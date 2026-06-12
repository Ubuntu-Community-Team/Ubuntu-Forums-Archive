---
title: "From Ubuntu to Win and back again"
date: 2006-01-22
forum: Absolute Beginner Talk
---

### Post by UbuntuKhan on 2006-01-22
Hello! I'm new to Ubuntu and linux and I have a weird problem with my Internet connection.
First I must say that I find Ubuntu fairly simple to use as an operating system. This is due not only to the system in itself but also to a lot of people sharing there's experiences in forums like this..
Down to the problem..
I am linked to the Internet through a cable modem linked to my computer through a net card. I use DHCP for connecting. I am dual booting with win98.
When I'm starting in Ubuntu (after night, with the modem and computer being unpluged) I have no problem getting connected, but if I reboot from win98 to Ubuntu I can't get to the Internet. Why is that?
Sometimes if I'm shutting down the modem and computer I am able to see the web, but sometimes I don't.
In windows I don't have this problems, I can get the connection whether I have started in windows or I have rebooted from linux to windows.
Is there a way to make linux connect to the Internet no matter in which system I start?
Thanks! (sorry for my bad english)

---

### Post by Tripmonkey_uk on 2006-01-22
I had the same problen myself just yesterday.
The next time u get ubuntu online, check out your ip address & the other connection details & write them down.
Change your connection to static ipaddress instead of trying to use DHCP.
It now connects every time for me without fail, even after going into Windows.
Rearly strange why it does it though :???:

---

### Post by UbuntuKhan on 2006-01-25
Thanks, I'll try what you've said later on.

---

### Post by cotcot on 2006-01-25
When you connect to the net you get a lease from your provider for an hour or so (mine is 2 hours). When you switch to the other operating system within this time you have to release the lease. In windows it is with "ipconfig /release" in command prompt. In linux with DHCP you can release your lease with "sudo dhcpcd -k eth0" (supposing your network card is eth0).

---

### Post by UbuntuKhan on 2006-01-27
@ cotcot. I've tried what you said but it didn't work:
> adrian@lor3:~$ sudo dhcpcd -k eth0
Password:
sudo: dhcpcd: command not found


---


---
title: "Creating development environment; adding IP addresses to the machine"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Rostok on 2007-03-30
Hello,

First of all, I’m new to Ubuntu (and Linux in general), so my problem explanation or questions may be too long.

I have a VMware Workstation running on Windows XP Pro, with one virtual machine with Ubuntu 6.10 Desktop as a guest operating system. I need to create a LAMP development environment so I can work and test my client’s web site. So far I have successfully installed Apache, PHP and MySQL, but now I’m facing troubles setting the working copy of my client’s web site.
His web site is actually a hosting service running on Slackware, which provides hosting and shopping cart for window treatments web sites (online selling of blinds, shades, shutters etc.). It is a custom made and it can provide everything an online window treatments retailer needs for business (product and client management, tracking orders, etc.). It has an admin section to for administering the service and maintain the client's accounts. Every client of this service has it's domain name to which an IP address is assigned by this service system and configured in a virtual host configuration file.

**Question**: How I can create virtual hosts in my dev machine and, more important, using specific IP address for each of them?
**Question**: How I can assign an IP address to each of my test clients on my machine? Basically I need just two IP addresses – one for the admin section (panel) of the hosting service and another one for one test client (web site). For example, I need admin with his own IP and I need test with his own IP. Both are pointing to different web sites/section of the hosting service in my PC.

Basically, I need to replicate the situation from the production server to my development machine. I need to be able to create virtual hosts in Apache and for each of this hosts to assign a unique IP address along with some test domain name.

Also maybe the problem in my situation is the fact that the production server is running on Slackware and I want to create a dev env on Ubuntu 6.10 which is running on VMware virtual machine on WinXP. But, I like Ubuntu, I can work only in graphical environment in Linux (I’m a new to Linux) and I don’t want dual boot/OS on my machine.

Hopefully I don’t sound too confused and my question are readable and understandable. Any help, instructions or given directions to follow or links to visit is greatly appreciated.


Thanks,
Robert

---


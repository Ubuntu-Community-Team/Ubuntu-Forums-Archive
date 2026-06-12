---
title: "Best way to set up remote access to check on status?"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by OfficeLinebacker on 2006-03-18
SO I am going to install Dapper on a 1MHz Celeron with 810e chipset.  Really just going to use it to fold.
 
It used to have Win98 and I have it at my mom's, and she wants me to not have the monitor sitting on the counter where it is.
 
The only other machine is hers, a Toshiba Satellite running XP Pro.
 
What's the EASIEST way to log on periodically to check CPU usage, say through top, and read a file (FAHlog.txt)?  That's about all I would need to do.
 
Is it as simple as "telnet ubuntu" from a DOS command line (assuming I call it "ubuntu?"  Or is there anything more to it?
 
Not too interested in installing some kind of software on the laptop, but if it's really easy I'd do it.
 
I have experience with PuTTy at work only, but it seems very complicated.
 
I am familiar with CLIs and such, but not entirely comfortable using an entirely new Linux distro box (at work I am on RedHat all day, but we have special aliases and shortcuts and whatnot set up and it's pretty different from having your own box that you build from scratch).
 
Thanks!

---

### Post by Zelut on 2006-03-18
if you want remote access on the terminal level to a Ubuntu machine you can install the following package 'ssh', which will allow you ssh access to the server.

You can then use puTTy to connect and login.  Just type the IP address of the machine and you'll be given a login prompt.  From there you can check your F@H stats and then log back out..

---

### Post by OfficeLinebacker on 2006-03-18
Can I just type the host name?  She's set up with a router that runs DHCP.

---

### Post by Zelut on 2006-03-18
you could type the hostname but you'd need to do a little more config on the outbound machine (something to tell it that hostname = $IP).

You should be able to find the IP on the recieving machine easily (ifconfig).  Then just basically do 'ssh IP'.  It should be something simple like 192.168.0.XX.

---

### Post by OfficeLinebacker on 2006-03-18
Uh, how can I find out what the IP of the target machine is if the only way to interface with it is through ssh?

I mean yeah, I am on this machine right now, but what's the guarantee that when the DHCP lease expires it won't get another one?

---

### Post by Zelut on 2006-03-18
Valid concern.  The way I setup my network was to run DHCP from the router but also setup the router to assign a specified IP per mac address.  This way the machine will always have the same IP.  If this is an option on your router you might want to try that.

Otherwise, if you only have a few machines you can probably take a good guess & find the right IP.  Example:

If your router starts on 192.168.0.1 and assigns addresses as .2, .3, .4, etc and you only have two machines, its going to have to be one of the first two addresses.  Does that make sense?

---

### Post by OfficeLinebacker on 2006-03-18
kuya,

Thanks for taking the time to have this dialogue with me.

Sounds like we're starting to get into more complex problems.

So the IP is now 192.168.0.105 .

The router is a D-Link DI-604

What are the chances of getting a differetn address in the course of normal operation?

In the event of power loss (blackout or blown fuse)?

---

### Post by Zelut on 2006-03-18
Well as long as it keeps that connection (no reboot, power loss, etc) it should keep that same IP address.  In the event that all of your machines reboot & all request an IP at the same time there is a good chance it will change.  At that point you can also easily login to your router config (normally found at 192.168.0.1) and look for what devices are connected.  On my router anyway this shows each machine & its current IP.

If you ever find that you can't connect to the IP that you thought it was you can check it this way.  I guess it can get tricky to have a headless machine with a changing IP, but I dont think it will cause you too many problems.

---


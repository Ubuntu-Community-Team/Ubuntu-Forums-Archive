---
title: "No internet after installing Fiesty or Gutsy"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by qu1et_ubu on 2007-12-19
Hello all you ubuntu junkies!  I hope you can help a complete newbie.

After installing Fiesty or Gutsy, I cannot connect to the internet.  Here is relevent info:

DHCP is enabled.

ping -c 10 127.0.0.1 

     works fine

ping -c 10 169.254.4.42 

     also works fine (I think maybe this is my local IP?)

ping -c 10 198.168.1.1 

     yields "destination host unreachable" for each ping
     same holds true for every IP I've tried, except for 
     loopback and the one above.

I should add that I have winXP installed on this same machine, and internet connectivity works fine when booted into winXP.  I am connected to the internet via cable modem by way of a linksys router, using ethernet (not wireless).

Thanks in advance for your help!

qu1et

---

### Post by anewguy on 2007-12-19
Do you know what type of wireless card you have?

try:

lspci     in a terminal window and paste the output back in a reply here.:)

---

### Post by LaRoza on 2007-12-19
What you gave signifies that the OS is not connected to the router, 169.254.x.x means that the comuter gave itself that address, because it couldn't get one from DHCP.

@anewguy The poster is on a wired network

---

### Post by LaRoza on 2007-12-19
Try: [http://forums.suselinuxsupport.de/index.php?showtopic=20236](http://forums.suselinuxsupport.de/index.php?showtopic=20236)

In Windows, the command "ipconfig /renew" would most likely fix this, I believe the solution in the link above would do the same.

---

### Post by anewguy on 2007-12-19
> **LaRoza said:**
> What you gave signifies that the OS is not connected to the router, 169.254.x.x means that the comuter gave itself that address, because it couldn't get one from DHCP.

@anewguy The poster is on a wired network

OOOPPPPSSSS - my bad!  Was answering another post on wireless and got that post confused with this one.  Please ignore my post!!   Sorry!!

---


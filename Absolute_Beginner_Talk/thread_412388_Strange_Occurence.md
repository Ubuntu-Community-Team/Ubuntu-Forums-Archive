---
title: "Strange Occurence"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-18
I just had a strange problem with ubuntu. My broadband connection completely failed on it. I couldn't even access the router page. I know the internet connection was working because my sister was using it on a different computer. I tried everything, checking cables and settings with no luck. I then booted up Ubuntu from its CD and the Internet worked on it!! I then thought that I was going to have to reinstall Ubuntu. However before I did, I switched the boot order back to the HDD and the connection was suddenly working again!! Does anyone out there have a possible explanation for what happened, and how to prevent something like this from happening. It scared the daylights out of me when I thought I might have to reinstall Ubuntu!!!

---

### Post by houstonbofh on 2007-04-18
Lots of things can cause a network stack to fall over.  Next time, get into a terminal.  Type 'ifconfig' and it will tell you some good information. (Like do you have a good IP address)  No IP address, or a 169.x.x.x one?  Type 'sudo dhclient' to get a new one.  You can also try name service.  Type 'nslookup' and you will get a '>' prompt.  Type 'google.com' and you should get an address.  No?  Type 'server 4.2.2.2' and try again.  You con go on like this a while.  Or you can reboot.  But I hate rebooting... :)

---


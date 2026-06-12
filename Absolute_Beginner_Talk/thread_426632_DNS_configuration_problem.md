---
title: "DNS configuration problem"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by chuypc on 2007-04-28
Hi y'all! This is my first time posting here. I have a question and I hope someone can help me. 
I use [OpenDNS]("http://www.opendns.com"), but every time I restart the machine, the DNS addresses go back to the original ISP . I already edited the resolv.conf file, but it doesn't keep the OpenDNS addresses. Can anyone help me?

Thank in advance!

Ups! I forgot to mention I'm using Feisty Fawn! Sorry!

---

### Post by [S|G] on 2007-04-28
From the OpenDNS Unix FAQ:

> 

Using OpenDNS with DHCP

If you assign your computer's IP with DHCP, it probably overwrites your /etc/resolv.conf. Here's how to fix that:

   1. Run: sudo gedit /etc/dhcp3/dhclient.conf
  
 2. Change the prepend line to read:

      prepend domain-name-servers 208.67.222.222, 208.67.220.220;

      This will prepend the OpenDNS addresses to the top of the list. (You can also use "supersede", which will just use them.) You don't have to worry about the DHCP client overwriting settings on each reboot or lease cycle, and your ISP nameservers will still be used as backup.

   3. Run: sudo /etc/init.d/networking restart

   4. Using Ubuntu? Check "Networking" to see if the changes applied correctly.
      Go to "System &#8211;> Administration &#8211;> Networking" and click the DNS tab.


---

### Post by chuypc on 2007-04-28
Thank you very much! That worked right away!

---


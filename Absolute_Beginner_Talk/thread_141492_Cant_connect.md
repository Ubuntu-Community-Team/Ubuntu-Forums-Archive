---
title: "Cant connect"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by Severedtoe on 2006-03-08
Maybe you guys can lead me in the right direction. I have a 2nd computer....connected to my ethernet moden thru a hub. My primary computer accesses the internet no problem (a WinXP machine). My 2nd computer I cant get online. I called my ISP and they can ping the IP addy of my primary machine but not my 2nd machine. My ISP tech support wanted to know if there is a built in firewall with this Ubuntu....well I have no idea. Perhaps one of you guys would be willing to hold the hand of an admitted "tech-tard" and help me thru this? My email addy is [email]severedtoe@gmail.com[/email] and I am on AIM as "severedtoeKoL"...any help would be greatly appreciated.

Thanks
~Toe

---

### Post by prizrak on 2006-03-08
You need a router that will server you an IP address in order for the other machine to work. It generally works like this 
- Your ISP's modem gives you an IP address
- If you have one computer its fine, but if you have more than one you need a way to share that one address, hub wouldn't work as it's in effect nothing more than a wire splitter. You need a router that will be seen as the only device with access to the internet. It sumiltaneously serves IP addresses to your local network. 
You can turn your WinXP machine into a router but that would require an extra NIC.

---

### Post by Severedtoe on 2006-03-09
I connected my Linux machine directly to my modem and it worked fine. So I went and purchased a router, followed the set up instructions to the letter and fired everything back up. The WINXP machine accessed the internet right away...the Linux machine I still cannot get online. I am at the point of abandoning this OS. If anyone out there can help me out I would be eternally greatful.

Toe

---

### Post by Severedtoe on 2006-03-09
OK....sorted it out....I had my networking properties set to static IP....changed it to DCHP, rebooted and there it is!

---


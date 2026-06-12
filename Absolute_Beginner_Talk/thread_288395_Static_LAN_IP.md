---
title: "Static LAN IP"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-29
I have a Linksys wireless g router and my ubuntu box is plugged into it. Im using my ubuntu box as a SFTP server and for ssh and Vnc. I wondered how I could give my computer a static lan IP.

---

### Post by JayTee on 2006-10-29
It's easy if you're using Gnome or KDE. If it's the server without a GUI I can't help you much. If you are using Gnome or KDE just go to the System|Administration menu and choose Network. Type the admin password and an applet will appear for your network settings. Select the Ethernet Connection in the Connections list and click on Properties. If it's set to DHCP (default) the IP addr, Subnet mask and Gateway will be grayed out. Click on the arrows on the Configuration listbox and it will let you select the Static IP setting and then you can fill in the the rest of the info below. I would assign an address between 192.168.1.2 to 192.168.1.99 as the Linksys by default reserves the addresses of 192.168.1.100-255 as DHCP leases. If you have any other computers using it like a laptop and they are set to DHCP this will avoid any conflicts if one of the machines is rebooted and it's lease had not expired.

---

### Post by Iowan on 2006-10-29
You can "manually" adjust (set) your IP settings by editing the **/etc/network/interfaces** file, although sometimes the **dhclient** program seems to keep running and reassign an address anyway,  I recently discovered how powerful the **ifconfig** command can be - I'll invite you to investigate via **man ifconfig**.

---


---
title: "Help : Unable to connect to the internet with Gutsy Gibbon"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Milind on 2007-11-16
I'm a long-time Win XP user and a complete Ubuntu newbie. About a month ago I converted my system into a dual boot one with Win XP and Ubuntu Feisty Fawn. Apart from minor teething troubles, things were going smoothly till yesterday when I changed it to a dual boot Win XP with Gutsy Gibbon. I did a clean install of Gibbon. Since then I'm unable to connect to the internet using Ubuntu. Using Win XP (as I'm doing to post this appeal for help) there's no problem whatsoever. I connect my home computer to the net using a broadband connection via a D-Link DSL 502-T router (*not* wireless ). 

Can anyone suggest how I can fix this? Please remeber that I'm a total noob. :(
Thanks in advance.

---

### Post by philinux on 2007-11-16
Is the network icon in the top right corner?

---

### Post by bumanie on 2007-11-16
There are numerous posts about this issue. I am unsure which solution is  is best for you. 
These are your options as far as I know
1) Upgrade your modem/router's firmware. I know that not all 502 t's firmware is compatible with ipv6 which has been added to gutsy. Firmware is available from d-link's web site. One forum member fixed the problem by doing this (not sure what brand of modem).
2)  Look at this link and decide if anything it suggests applies to you and whether you are happy to follow their suggestions. [http://www.lockergnome.com/linux/](http://www.lockergnome.com/linux/)
3) Search past forum queries by typing your query in the box at the top right hand corner of the page.
Good luck. I would suggest trying the firmware upgrade first, so as not to alter your new system too much.

---

### Post by mamlouk on 2007-11-16
If you can ping your router from a terminal window, then probably you have your IPv6 enabled system-wide. 

To confirm that, open your Firefox, and type in the address bar ```
about:config
```. In the filter, type in "ipv6" without the quotes, press enter,  and double-click "network.dns.disableIPv6" to disable it in Firefox only. Restart Firefox and check for internet connectivity, if it works, then re-enable it and check this [video](http://www.youtube.com/watch?v=Sd8nHsUevAY) to disable it system-wide.

I addition to that, I blacklisted ipv6 as well by doing a ```
sudo gedit /etc/modprobe.d/blacklist-ipv6
``` which will open a new file, type in that file ```
blacklist ipv6
```, save, close and restart.

Good luck.

---

### Post by jw5801 on 2007-11-16
> **mamlouk said:**
> If you can ping your router from a terminal window, then probably you have your IPv6 enabled system-wide. 

To confirm that, open your Firefox, and type in the address bar ```
about:config
```. In the filter, type in "ipv6" without the quotes, press enter,  and double-click "network.dns.disableIPv6" to disable it in Firefox only. Restart Firefox and check for internet connectivity, if it works, then re-enable it and check this [video](http://www.youtube.com/watch?v=Sd8nHsUevAY) to disable it system-wide.

I addition to that, I blacklisted ipv6 as well by doing a ```
sudo gedit /etc/modprobe.d/blacklist-ipv6
``` which will open a new file, type in that file ```
blacklist ipv6
```, save, close and restart.

Good luck.

What's with the creating a new blacklist file?! Open /etc/modprobe.d/blacklist and append the line blacklist ipv6 to the end. Or just run:
```
echo blacklist ipv6 | sudo tee -a /etc/modprobe.d/blacklist
```Then reboot and you should be working again.

---

### Post by Milind on 2007-11-16
mamlouk and jw5801 
Many thanks. I disabled ipv6 system-wide as shown in the video suggested by mamlouk and then ran the code jw5801 had suggested. The problem's solved and I can now connect to the internet. In fact, I'm posting this using Ubuntu 7.10. Thanks again for your prompt help. :)

---

### Post by Milind on 2007-11-18
Perhaps I jumped the gun a bit here. After doing the above I can connect to the net and browse without a problem but the Update Manager fails to download anything and gives error messages. I cannot connect to any update servers. ? time out ? network problem .

---

### Post by zaigham_tt on 2007-11-18
:popcorn:

---

### Post by Skefflock on 2007-11-18
> **Milind said:**
> Perhaps I jumped the gun a bit here. After doing the above I can connect to the net and browse without a problem but the Update Manager fails to download anything and gives error messages. I cannot connect to any update servers. ? time out ? network problem .
What exactly does it say? I had an issue with downloading upgrades and it was so silly one, just coz system wasn't able to connect to the net during the installation process it did configure the synaptic the way only the original cd was considered as a package source, none of the repository did. So I just added standard repositories from gui menu and it worked.

---

### Post by jw5801 on 2007-11-18
> **Milind said:**
> Perhaps I jumped the gun a bit here. After doing the above I can connect to the net and browse without a problem but the Update Manager fails to download anything and gives error messages. I cannot connect to any update servers. ? time out ? network problem .

Please post: ```
cat /etc/apt/sources.list
```

Occasionally the servers do go down, so if you aren't experiencing any other issues, this is quite possibly the case. You can also try using the ftp servers as opposed to the http. Sometimes one works where the other fails. ftp is much more effective at working through firewalls for example.

---

### Post by jimbean on 2007-11-18
how about going into
system
administration
network
and make sure you have
the correct connection checked
then make sure the properities
are set to automatic dhcp

---

### Post by LizardKing73 on 2007-11-18
I had the same update error problem, fortunately its an easy fix.
Go into System > Administration > Software Sources
U'll be asked for u'r password
When the window comes up make sure all the boxes on the Ubuntu Software tab (opening page) are checked then click on the Updates tab and make sure all the boxes there are all checked.
Restart and u should get an Updates Available prompt and everything will start working the way it should.
If for some reason u dont get an auto update prompt try running update manager

---

### Post by mamlouk on 2007-11-19
I think the same happened to me after installing Gutsy. I tried playing around with the repositories and found out that sometimes it works, and sometimes it doesn't. I found out that it was a name resolution problem. Open a terminal window and type ```
sudo apt-get update
``` If it stops at the first repository trying to resolve it's name, then here's your problem. To make sure it is, type that in your terminal window ```
host ubuntuforums.org
``` it should return something like ```
ubuntuforums.org has address 91.189.94.186
ubuntuforums.org mail is handled by 10 mail.ubuntuforums.org.
``` If it gives you an error then try typing in your name servers as your preferred DNS servers instead of the ones assigned by DHCP. To do that, it would be better to assign a static IP address by editing your interfaces file by ```
sudo gedit /etc/network/interfaces
``` Change the section where it says ```
iface eth0 inet dhcp
``` to ```
iface eth0 inet static
	address 192.168.1.5
	netmask 255.255.255.0
	gateway 192.168.1.1
``` Where eth0 is your connected NIC, and change to your relevant IP address, subnet mask and gateway. Then ```
sudo gedit /etc/resolv.conf
``` and type in your relevant preferred DNS servers using the following syntax ```
nameserver 100.100.100.100
``` You can probably find out your ISP assigned DNS by logging on your router's web interface and checking it out.

---

### Post by Milind on 2007-11-19
> **Skefflock said:**
> What exactly does it say? I had an issue with downloading upgrades and it was so silly one, just coz system wasn't able to connect to the net during the installation process it did configure the synaptic the way only the original cd was considered as a package source, none of the repository did. So I just added standard repositories from gui menu and it worked.

While I don't remember the exact wording of the error messages, basically it couldn't connect steadily to any server and almost never to the main one. I did add the usual repositories using the "Software Sources" gui including testing for best server and using that but without any luck. After banging my head against the problem for a long time trying this and that I finally went back to Feisty Fawn in frustration. Since yesterday afternoon I've been trying to re-install Gibbon without success. The installer gets to 'inspecting file system' and hangs at 15% (tried four times!). Will try again today or tomorrow when I have some time. ](*,)

---

### Post by Milind on 2007-11-19
@mamlouk :
Thanks for the detailed reply. Please check my reply to Skefflock above. Once (or should I say if ?) I get Gibbon iinstalled again I'll certainly give this a try.

---


---
title: "Installing Ubuntu on external USB HDD"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by norman.mcfarlane on 2007-02-10
Gooday all,
I have successfully installed a LAMP Server, but I want to lean more about Linux/Ubuntu as in working at the command line.
I find it frustrating and confusing, since I cannot find anything simple that explains how to edit the network setup. For e.g. I want to change the LAMP Server from DHCP to fixed IP, since i want to use it as a web server and database server amongst others. Try as I might I cannot find anywhere that tells me what file to edit to change the network setup.
Rightly or wrongly I have concluded that I need an installation of Ubuntu on which I can "fiddle" without causing a disaster. I have a HP NX6110 notebook, with a USB External HDD, 80GB in size. It is an NTFS drive, with a single partition. I've already changed the CMOS to give me the option of where to boot from at system start up, but from here I get a bit hazy, as to how I actually do the install on the USB Drive.
Can somebody point me in the right direction?
Also, is there a good HTML or PDF Linux Tutorial/User Guide/Reference that I can download onto my PDA (Nokia 9300) which will give me the guidance that I need in working with Bunut/Linux at the command line.
Any help will be much appreciated. I leave on a trip tomorrow (Sunday) so some guidance before I leave will be much appreciated.
Regards,
Norman

---

### Post by Jussi Kukkonen on 2007-02-10
> Try as I might I cannot find anywhere that tells me what file to edit to change the network setup
*/etc/network/interfaces*. A basic one would look like this:
```
auto lo eth0
iface lo inet loopback
iface eth0 inet static
        address 192.168.0.104
        netmask 255.255.255.0
        gateway 192.168.0.1

```
More info: *man interfaces*

---

### Post by norman.mcfarlane on 2007-02-10
Thanks so much, Jussi! It works just great! No more DHCP, and i also have two ethernet devices configured and starting successfully.
All in now need to do, is figure out how to bridge teh two interface so that I can stick my ADLS modem on the one and use my Ubuntu box as a gateway instead of using my MS Windows Server 2003 box, which is so SLOW!
Regards,
Norman

---


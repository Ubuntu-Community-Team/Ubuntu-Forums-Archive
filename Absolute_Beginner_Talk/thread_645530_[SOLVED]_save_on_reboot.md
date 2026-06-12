---
title: "[SOLVED] save on reboot ?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by r4ik on 2007-12-20
This is what i did ,

1. Open a terminal window and type the following.

    $ sudo network-admin

Note: Root access is required for this step.
2. Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers.

    208.67.222.222
    208.67.220.220

To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0

Still after a reboot it is back to 192.168.1.1

how do i make it "stick" ?

thanks

---

### Post by HereInOz on 2007-12-20
You may be getting done in by network manager trying to reset the ip addresses on reboot.

You most certainly need to untick roaming mode in the network properties in the network-admin dialog box, then set your static ip address and static dns addresses.  That ought to do it.  If you leave roaming mode ticked, you will be forever frustrated.

If that doesn't work, you could try uninstalling Network Manager totally.

---

### Post by r4ik on 2007-12-20
Thanks for you're reply i will try as suggested and let you know.

---

### Post by r4ik on 2007-12-20
I removed metworkmanager and it left me disconnected. 
Roaming is off still no go  :(

---

### Post by r4ik on 2007-12-20
Nice and friendly bumpy :)

---

### Post by jken146 on 2007-12-20
Did you try puttitng your static IP and DNS in network manager?

---

### Post by r4ik on 2007-12-20
Sorry i didnt and i have not got a clue howto can you give me some pointers please,networking is not my thing.

---

### Post by jken146 on 2007-12-20
Click on Network Manager, click on Manual Configuration, enter your password, go into Properties for the connection you want to use, disable Roaming Mode, and put the details you had in your first post in the boxes.

---

### Post by r4ik on 2007-12-20
Well it is faster now i used my own Dns'es thanks for you're time and effort !
(cant figure out why the dhcp does not stick but i will save it for a rainy day :) )
Thanks again !

---


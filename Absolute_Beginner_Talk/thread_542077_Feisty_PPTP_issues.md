---
title: "Feisty PPTP issues"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by getut on 2007-09-03
Hello, I am trying to set up a VPN connection in Feisty. I had one working in Edgy the old supposedly hard way, but am having trouble Feisty's new improved way.

I am following this tutorial:
> Ubuntu Feisty

    * install the network-manager-pptp package, and if it was not already installed, restart the network manager applet and Network Manager:
          o right-click the network icon on your system tray and choose Remove,
          o Alt/F2, run nm-applet, and the network icon will return,
          o restart Network Manager:
            sudo /etc/dbus-1/event.d/25NetworkManager restart
            sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher restart

    * left-click network icon, choose VPNS then configure, then add a VPN with the wizard,
    * left-click network icon, then VPNS then the VPN you created,
    * watch the logs to see if it worked:
      sudo tail -f /var/log/syslog

Reference: PPTP From Ubuntu, by Stephen Thorne.

I have the network-manager-pptp package installed but the next step isn't like it says it should be.

If I right click the icon, I don't get an option to remove the applet. All I get is a drop down box with "Enable Network" "Connection Information" and About. There is no option to remove it. I did get it removed one time, but it seems that the icon is in grouping called "Notification Area" and is not by itself. When I did get it to go away, the whole notification area went away. I have restarted multiple times and I never get the option to remove, and either left clicking or right clicking never brings up the VPNS option either.

Please help.

---

### Post by igel on 2007-09-04
The same happens to me. The only effect is I have applications->internet->vpn connections manager and I've set my connection there but there is no way to start it.

---

### Post by gfarrow on 2007-09-06
I have the exact same issue.    I have Applications>Internet>VPN Connection Manager(PPP Generic), but Network Manager gives me no options to do anything with VPN.  If I left click it the only option is "Manual Configuration" and when I bring that up I just have my regular network settings, nothing related to VPN.

Also selecting the VPN Connection Manager from the menu doesn't launch anything, but if I execute the command manually from a terminal it does bring up the VPN Connection wizard and I can create a VPN connection.  I just have no way to start it.

Also when I execute the VPN Connection Manager command from the terminal I get the following message repeated several times, although the wizard still comes up:

** (nm-vpn-properties:6022): CRITICAL **: vpnui_opt_connect_signals: assertion `opt->widget!=NULL' failed

This is a real pain in the butt.  I also had this VPN connection working in a previous release using the old "hard" method.

---

### Post by getut on 2007-09-07
Please.. can any guru help with this? Multiple people with the issue. What are we doing wrong?

---

### Post by Sheik Yerbouti on 2007-09-09
OK so I just figured this out myself and it was a complete pain in the ***. So no gaurantees or anything. So it seems as though this is quite buggy. For one the VPN option does not show up on the network manager applet once installed if you are using a static IP or don't have roaming mode enabled for the interface.

Also there are two ways to manage your network connection to say change it back to DHCP. One is left click on the nm-applet and click manual configuration and make changes. And the other is through the menu system >> administration >> network. Here's another bug they don't synch up for some reason. So if you go to the menu system >> administration >> network change it to DHCP and reboot. Once your back up nm-applet still acts like you are on a static IP it still says manual configuration. 

What I had to do was enable roaming mode for the interface. And then killall nm-applet then alt-f2 run nm-applet and the run these commands

sudo /etc/dbus-1/event.d/25NetworkManager restart
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher restart

Keep in mind this was AFTER I had switched BACK TO DHCP and enabled ROAMING MODE for the interface. Then the VPN menu option showed up.

Good luck you will need it.

---

### Post by gfarrow on 2007-09-11
I tried switching to DHCP from a static IP and enabling roaming mode as per the previous post and I was able to get the VPN Connections menu to show up on NetworkManager, but only after rebooting.  Restarting the nm-applet, NetworkManager, and NetworkManagerDispatcher had no effect until I rebooted.

Obviously a bug in NetworkManager since the ability to use VPN should have nothing to do with whether you are using a static IP or DHCP.

---

### Post by getut on 2007-09-11
I'm going to have to build a DHCP server machine to even try it out.

I'm on a wired network that hooks to a wireless bridge to a remote wireless router. The router will not give out IP addresses to wired computers behind the bridge. The DHCP offers only work for wireless clients directly connecting to the wireless router.

So with network configuration and its limitation, the only way I can go DHCP is by putting a DHCP server behind the bridge. All just to get a VPN working.

I'm sure glad Sheik Yerbouti discovered the link between static IP and the problem though. When you don't even know where the problem IS, then it impossible to create a workaround.

---

### Post by Sheik Yerbouti on 2007-09-11
Just FYI I went to file this as a bug and found this when trying to file it.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/114700](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/114700)

---

### Post by byenary on 2008-02-06
Having the same problem, everything is fine when wired, but when connected wireless i can not get the vpnconnection option to appear...

---

### Post by byenary on 2008-02-09
Need to enable roaming ...

---


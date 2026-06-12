---
title: "Problems Setting Up Samba"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-11-10
I am trying to set up a shared folder on my computer (which runs Ubuntu Dapper) which can be accessed by another PC which runs Windows 2000.  The first time I had to do this, I used this guide: [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605).  It worked fine, the shared folder was visible under the network settings.  However, I had to reinstall Windows 2000.  After following the same guide again after reinstallation, the shared folder is not visible under Windows.  I can see the "ubuntu" pc but there is no shared folder under it.  :confused:  I've set up this several times so I don't think I have mistyped a setting.  

Any help would be greatly appreciated.  :)

---

### Post by dannyboy79 on 2006-11-10
ok, have you done all this;
2. Changing network settings in Windows

Now we should let Windows know that there's a WINS server active in the network. 

If you had to change "wins support" to "no" above skip this step!

- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
- Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in the ip-address of your Linux box
- Click "Add"
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot Windows

Upon reboot you may now map the network drive within Windows.

With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
NOTE: Adjust this to the hostname and sharename you chose above!
- Click "Finish"

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.
- Click "Finish"

That's it - samba is up and running now.

When you reinstalled Winbloz, did you setup a user with the same exact name and password as you already have on Ubuntu? did you winbloz computer get a different ip than before and maybe some firewall is blocking it? Can you first of all ping your computers from one another by name and by ip? that would be the first goal, until that can happen, there is no point in working on samba, samba assumes you have the computers already communicating over tcp/ip.

---

### Post by fatsheep on 2006-11-10
Looks like Zone Alarm was blocking it.  Shared Folder works now, just gotta set up the printer...

---


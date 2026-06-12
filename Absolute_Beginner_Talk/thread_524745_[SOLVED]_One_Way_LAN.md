---
title: "[SOLVED] One Way LAN"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Robert Ashley on 2007-08-13
As a newcomer to Linux, I am having trouble getting a Local Area Network to communicate in both directions.
Ubuntu Linux Ver 7.04 is installed in a dual boot configuration with Win XP.
I also have a Macintosh iMac and a 4 port router, all connected together, with ethernet cabling.
The iMac and Win XP communicate properly both ways.
From Linux, I can communicate with the iMac by selecting "Places" in the top menu bar, then "Network", wait about 20 seconds, then select "iMac", then "Connect as user" and press return. This probably is not the best way to do this, but it does work.
When I try to communicate from the iMac to Linux, I select "GO" from the top menu bar, then "Connect to server", then enter "smb://192.168.1.101" (PC ID#)
and press "Connect" I get a window with "Select the SMB/CIFS volume you want to connect to", and a smaller window with the folder on the Linux Desktop named "XFER" (The Share folder I created), and an "OK" button.
Pressing "OK", I then get another window titled "System Authentication", with the common domain "MSHOME" and my user name already shown. It asks for my password, and has another "OK" button. Pressing "OK" I then get the message
"Could not connect to the server because the name or password is not correct."
I am assuming that it is the password that is causing the problem.
I have searched through many folders in the Linux installation and found "smb.config".
I have edited this file as best as I could to apply to my system.
The response to "testparm" after editing is as follows;

bob@Linux:/etc/samba$ testparm smb.conf
Load smb config files from smb.conf
Processing section "[homes]"
Processing section "[Xfer]"
Loaded services file OK.
Server role: ROLE_DOMAIN_BDC
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        interfaces = 192.168.1.1/8, eth0
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        domain logons = Yes
        domain master = No
        dns proxy = No
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No

[Xfer]
        comment = File transfers
        path = /home/bob/Desktop/Xfer
        read only = No
        guest ok = Yes

In the "Authentication" section of "smb.conf" there is a reference to "/Samba3-HOWTO/ServerType.html".
I read this file, but there are so many options for security types and levels, that I don't know the proper choices.
This Authentication section also states that all users accessing this server must have a "Unix" account. I don't know how to do that either.
Any help in getting the correct settings for two way communication over my LAN, will be sincerely appreciated.
Thanks, Bob

---

### Post by amsterdam on 2007-08-13
Did you set your samba passwords? There is a awesome FAQ written on samba

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

keep us posted!

---

### Post by Robert Ashley on 2007-08-14
Many thanks for your reply to my LAN problem.
I tried to follow your instructions, but still have the same problem in not being able to access Linux from my Macintosh.
First, my ISP requires the interface to be DHCP, no static addresses.
After editing the "smb.conf" file according to your instructions as best as I could, doing a "testparm" on smb.conf, the response was:

bob@Ubuntu:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
Processing section "[Xfer]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = 
        interfaces = lo, eth0
        bind interfaces only = Yes
        null passwords = Yes
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        printing = cups
        print command = 
        lpq command = %p
        lprm command = 

[Xfer]
        comment = File transfers
        path = /home/bob/Desktop/Xfer
        force user = bob
        force group = bob

Hopefully you will see something wrong with this group of settings, and can suggest a correction.
Thanks again.

---

### Post by amsterdam on 2007-08-14
It sounds like samba is *working* but for some reason you are not authenticating properly. You look good up to where you have to enter your password, in which it says "Could not connect to the server because the name or password is not correct." 

have you tried running this:

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

replace your_username with the username on the ubuntu machine. (looks like bob) and make sure to use the same password as your ubuntu account

lets restart samba just to make sure
sudo /etc/init.d/samba restart
***

if that does not work try adding
        read only = No
        create mask = 0644
right below
        force group = bob

let us know how it goes!

---

### Post by Robert Ashley on 2007-08-15
Hey!! Many thanks, It's working now.
I restarted as you suggested, and then the "sudo smbpasswd -L -a user_name" and again with "-e".
The restart must have been the key, as I had previously followed the "sudo smbpasswd..." in your instructions.
I really appreciate your help!
Bob

---


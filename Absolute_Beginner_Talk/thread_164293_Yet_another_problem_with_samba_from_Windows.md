---
title: "Yet another problem with samba from Windows"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by kt226 on 2006-04-22
I have isntalled Brizzy and samba on a PC to act as a file storage. I have created samba users and passwds in order to connect to my Ubuntu box through XP. 

I have edited smb.conf and the workgroup is MSHOME.

Then I go to my XP (firewall disabled) and I try to view workgroup computers. The samba box does not appear. 
 in the address I put \\aeolos-media and I can then access the samba box. I gibe username passwd and everything works fine.

I can do the same under run: \\aeolos-media.

So for some reason the samba box does not appear in the workgroup (all computers are in workgroup:MSHOME).

Furthermore, when I access the samba box as above I get the title: Media Server (aeolos-media), as it should since in the smb.conf I have netbios name = aeolos-media and server string = Media Server.

However when I access the samba share the title changes to my_media on Samba 3.0.14a-Ubuntu (aeolos-media).

In addition when I access the samba box through \\aeolos-media the title on the login box is: Connect to localhost.localdomain

Abobe the user name box: Connecting to Aeolos-Media.

When I go to my linux box->Network Settings->General I have:
Hostname: aeolos-media
Domain Name:MSHOME

In the hosts tab among other things I have:
IP Address           Aliases
192.168.0.11       aeolos-media
127.0.0.1            localhost.localdomain localhost aeolos-media

I have tried to change the order of aliases in 127.0.0.1 to put aeolos-media first, but it always reverts back to the above.

I am not a Linux expert but I have managed to set-up Samba several times before in both RedHat and Suse. I never had this problem before. Do you think that I am missing smth or there is a problem elsewhere?

Any help will be greatly appreciated.

Thanx a lot

Kostas

---

### Post by AndyCooll on 2006-04-22
This website might give you a few clues, perhaps you've missed something:
[Setting Up Samba]("https://wiki.ubuntu.com/SettingUpSamba)

:cool:

---

### Post by Zhukov on 2006-04-24
Define the workgroup and add this to your samba conf:

############################# ADICIONADO A UNHA
interfaces = 192.168.0.0/255.255.255.0 127.0.0.1
bind interfaces only = Yes
netbios name = FANTASMAS
socket options = TCP_NODELAY IPTOS_LOWDELAY
local master = yes
os level = 65
domain master = yes


Note:
Set the ip range to suit yours, as well as the NETBIOS (use the same as the workgroup name)
The os level defines this machine as the "boss" because Windows machines can only go as high as 32.

---


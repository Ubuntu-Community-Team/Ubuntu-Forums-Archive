---
title: "Connecting to a VPN"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-02-22
I need to connect to my University's Vitrual Private Network. I have loacted and dowlaoeded a cisco vpnclient but i am utterly stuck...

HELP!!!

---

### Post by oakz on 2006-02-22
Not sure where you are stuck, but here is how to install it in a nutshell...

After you downloaded the cisco VPN client, did you expand the file? If not, do the following from a terminal:

$ tar zxvf vpnclient-linux-4.8.00.0490-k9.tar.gz

This will create a directory named vpnclient (at least the package I have does). cd into that directory.

You next need to run the provided init script. This will compile a kernel module that handles the VPN traffic. In order to work, you need to install gcc-3.4 and the linux-headers package for your current kernel.

Once those are installed, run the init script:
$ sudo ./vpnclient_init

Follow the instructions it prints at the end to manually start the vpn service (it will start automatically from now on when you reboot). 

You need to then create a profile for the VPN you want to connect to, and put the file in /etc/CiscoSystemsVPNClient/Profiles (there is a sample.pcf profile to get started with already in that directory)

Hope that helps!

---

### Post by MartinJ on 2006-02-22
My university also uses a Cisco VPN client, I have the windows version installed on another partition of my computer.

To get it working in kubuntu I installed the kvpnc package using apt-get and then imported the .pcf profile from the windows partition.  This set up the VPN correctly and all I need to do is enter my password.  Works great and easy to use!

a request for more information:

1. The Cisco VPN profile information is installed at c:\Program Files\Strathclyde VPN client\VPN\profiles\Academic Network.pcf
2. I copied this file to my home directory
3. Used KVpnc to import pcf profile (tick decode secret button when asked)
4. Click connect and enter username and password.  Leave group password alone.

I used to have problems with group password not being correct, but it now works.  Strange.
If you don't have a pcf file you'll need to speak to the vpn admin or helpdesk because you need an ip address and the group password.  My pcf file is listed below (with some text removed).

```

[main]
Description=connection to Strathclyde Academic Network
Host=130.1.."IP address of university VPN entry point"
AuthType=1
GroupName=entry
GroupPwd=
enc_GroupPwd=290EA7A36046B......"encoded group password"....C44E
EnableISPConnect=0
ISPConnect=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
EnableMSLogon=1
MSLogonType=1
EnableNat=1
CertStore=0
CertName=
CertPath=
DHGroup=2
ForceKeepAlives=0
PeerTimeOut=90
ISPConnectType=0
ISPCommand=
Username="my username"
BackupServer=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
EnableLocalLAN=0

```

Hope that helps... :)

---


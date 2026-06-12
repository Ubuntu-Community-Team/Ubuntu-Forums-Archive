---
title: "Help with vpn"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-09-01
I need to connecto to a vpn for school, I've been trying to use Kvpn, with no success.  I recieve an error saying:

> Loading of module "tun" failed!

I'm not quite sure if I'm configuring all the settings correctly.
I've recieved instructions for a cisco vpn.  I was given a .pcf file to use, but I'm not sure where it goes, or if it could be used on anything other that Cisco VPN client.

.pcf
> [main]
Description=U*** ***
Host=****.***.***.***
AuthType=1
GroupName=***
GroupPwd=****
EnableISPConnect=0
ISPConnect=
ISPCommand=
Username=
SaveUserPassword=
EnableBackup=0
BackupServer=
EnableNat=1
CertStore=0
CertName=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
DHGroup=2
ForceKeepAlives=0

I obviously blocked out the obvious things that shouldn't be seen by others, but where exactly do I put this file, or configure the settings?  Hopefully someone out there can help me out. Thanks.

---

### Post by meng on 2006-09-01
Go with installing vpnc, which works well with Cisco concentrators. You can google (or maybe search these forums) for how to set up a configuration file for the connection. It is a command-line application, but may work with kvpn as a front-end (I'm not sure about that).

---

### Post by CeeDub on 2006-09-02
I tried vpnc. After I typed in all the information I got this error:

vpnc: binding to port 500: Permission denied

I typed all the infromation correctly.  What could be wrong?

---

### Post by CeeDub on 2006-09-02
bump.

This is kind of important for me.  Anyone have a clue?

---

### Post by meng on 2006-09-02
sudo vpnc
Be patient, answers in this forum take a while.

---

### Post by blx_286 on 2006-09-12
> **CeeDub said:**
> vpnc: binding to port 500: Permission denied

I got that also. Try using **sudo vpnc**. Also in /etc/vpnc there is a example.conf file. You can copy it, fill in the blanks and use it as so ... **sudo vpnc example.conf**

I can't get the Cisco client or VPNC to work. Here is what I get with VPNC:

username@homepc:~$ sudo vpnc --debug 2 --no-detach

Enter IPSec gateway address: xxx.xxx.xxx.xxx
Enter IPSec ID for xxx.xxx.xxx.xxx: work_id
Enter IPSec secret for [email]work_id@xxx.xxx.xxx.xxx[/email]:
Enter username for xxx.xxx.xxx.xxx: username
Enter password for [email]username@xxx.xxx.xxx.xxx[/email]:
vpnc version 0.3.3
S1
S2
S3
using interface tun0
S4
S4.1
S4.2
S4.3
vpnc: no response from target

ggggggggggrrrrrrrrrrrrrrr ](*,)

---

### Post by Spankmaster79 on 2006-09-14
I would also know if it works, since I need to use vpn. This keeps me from completely removing the Windows 2000 partion from my old Toshiba Tecra 8000

---

### Post by moore.bryan on 2006-09-14
*i don't know your situation, but the cisco server at my office won't accept linux connections; that was my problem.*

---


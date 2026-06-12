---
title: "Windows 7 + Samba = Headache"
date: 2011-04-19
forum: Any Other OS
---

### Post by ITMANAGER on 2011-04-19
Hello,
 
I know there is lots of info out there regarding accessing Samba shares with Windows 7 but I have tried what I believe to be everything with no joy (changing Windows 7 registry settings to accept blank passwords and use NTLMV2 session security if negotiated).
 
If I run XP mode, I can map the Samba share. From Windows 7 pro, I can not. When the incorrect Log-on details are entered, it says 'The specified network password is not correct' with the correct log-on details, it says 'Access is denied'.
 
The 7 Pro desktop is part of the SBS 2003 domain and the Ubuntu 10.10 is used only as a file server. I have made a few amendments to the SMB.CONF settings, sometimes with detrimental effects to the XP users. :(
 
Any one got any step by step instructions I could try on a Virtual Ubuntu Desktop with Samba? :confused:

---

### Post by Ghost|BTFH on 2011-04-20
> **ITMANAGER said:**
> Hello :confused:

Here's a quick question - are you attempting to log the Windows 7 machine into a domain?  Because quite bluntly - it doesn't work with samba.

However, that being said, just simply going to where they are \\ip.address\location and mapping them should be as simple as a right click.

So, for clarification, where are you getting an L/P request?

Cheers,
Ghost|BTFH

---

### Post by ITMANAGER on 2011-04-21
Hello,
 
 
The Domain controller is Server 2003. Ubuntu is only used for file sharing. When I try to map the folder with '\\10.10.10.100\SHARE\' when the correct details are entered, I get an 'ACCESS IS DENIED' response so the Windows 7 computers can clearly see the share but can not authenticate to.
 
I am now in the process of setting up a VM with ubuntu and Samba so I can change the smb.conf without affecting the XP users to see if it is a ubuntu smb.conf issue or a Windows 7 regedit problem.
 
Thanks for your response.:)

---

### Post by ITMANAGER on 2011-04-26
SORTED.
 
I started with a new UBUNTU install and fresh SMB.CONF file. Windows 7 could see and write to. I am now applying security settings checking after each change everyone can see it.
 
:)

---

### Post by Cheetah05 on 2011-04-26
There is some crap on the internet whereby there go into great depth about things, took me ages to figure out all I needed in my configuration file was.

```

[global]
workgroup = WORKGROUP
netbios name = FILESERVER
[shared]
path = "/path/to/folder/"

```

Then you just use your Ubuntu login to access the files....I don't think there is anything wrong with it security wise...but I'm sure someone will come along and correct me.

Access it in Windows 7 by : "\\FILESERVER\shared\"

---

### Post by pricetech on 2011-04-26
I haven't edited an smb.conf in ages.  I install system-config-samba via Synaptic, which installs both Samba and a GUI configuration tool which I use to configure my shares.

Never had a problem with XP or 7.

---

### Post by crispy_420 on 2011-04-27
Since you have a domain controller couldn't you map the drive to the Windows server and publish shares via active directory?

---


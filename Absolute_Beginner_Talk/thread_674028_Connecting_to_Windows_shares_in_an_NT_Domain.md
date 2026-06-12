---
title: "Connecting to Windows shares in an NT Domain"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by runemol on 2008-01-21
Hi,

I'm having big problems when I am to connect to a Windows share on a server within a Windows NT Domain. I get the authentication dialog prompting for a username, domain name and password in Nautilus. When I type the correct information and click "Connect", I do not get connected.

I've also tried to use smbclient from the console:
smbclient -L name_of_the_windows_server -U my_username
Password: 

yielding the following error:

session setup failed: NT_STATUS_PASSWORD_EXPIRED

The really annoying part of this is that this actually worked out-of-the-box, but I messed up my system and I'm now unable to make it work again.

Based on this I have several questions:
- Do I need kerberos authentication for this purpose?
- Do I need winbind for this purpose?
- What is the default configuration in order to be able to browse and read/write files on a Windows share within a domain?

I'm running Ubuntu Gutsy Gibbon.

Kind regards,
Rune

---

### Post by Thund3rstruck on 2008-01-21
I cannot comment on a NTDomain specifically but I have used Win2K & Win2K3 Active Directory environments for years as well as direct connecting windows and unix machines on domains and workgroups.

To make things as simple as possible go to the NTDomain and set a new password for the user. 

Then go to the Linux machine and create a new account where the username and the password are identical to the NTAccount. 

Now log into the linux machine with this new account and run smbclient. 
```

$ smbclient -L ipaddress

``` 

This will ask for the password and dump the SMB data for the client. After validating the domain in the dump (the domain will be the remote machine name if it's not attached to a domain) Go to Places > Connect to Server. Select Windows share and enter the required info. Enter all the fields except "folder" and click connect. 

This should establish the connection. 

To map shares dynamically or by user then you'll use the smbfs tools:
```

$ sudo mount -t smbfs //server/share /your/mount/location -o username=$(whoami)

```

Hope this helps.

---


---
title: "Can't Access Linux from XP"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by keith3232 on 2008-04-18
Please forgive my ignorance, I'm very new to the world of Linux (although I must say it's been a pleasent struggle so far). Here is the senario... I have a server running Ubuntu gutsy, which logs into a Windows domain. The Linux box is a database (running postgreSQL and postGIS)/data storage server. I have everything setup correctly (or so I thought), all other machines on the domain can connect to the server and the databases. The problem is, every morning when I boot up my XP machine I get a message telling me that it couldn't connect to all mapped drives. When I try to access the Linux server from My Network Places or the mapped drive I am prompted for a password. Restarting Samba doesn't help, but if I reboot the Linux machine, everything works fine (until the next morning of coarse). This problem occurs on all the other Windows machines on the network. I have one more server setup with Suse Enterprise 9, and it can connect to the Ubuntu server. What really confuses me is the fact that I can connect to postgreSQL from all machines on the network, just not from Windows Explorer. I have know idea what I should do next, so I would certainly appreciate any advise.

Keith

---

### Post by arochester on 2008-04-18
[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)

---

### Post by quirks on 2008-04-18
@arochester: I think what keith3232 is trying to do is not access a **local **Linux partition, but he is trying to access a remote share using Samba. So your suggestion, arochester, probably doesn't apply here.

@keith3232: the problem has nothing to do with any network connectivity issues (I'd say), because you can connect to other services on the Ubuntu server (e.g., PostgreSQL)  just fine. I suppose that the Windows machine fails to authenticate to the Ubuntu server. It might help, if you have a look at the Windows Event Log. Go to start -> Control Panel -> Performance and Maintenance -> Administrative Tools -> Event Viewer. There are several logs. Better look in all of them and scroll to the moment, where you logged on to your Windows machine. Maybe you can find some hints there.

quirks

---

### Post by Paqman on 2008-04-18
It's a known problem with Windows XP. I get the same with shares from my NAS. If you remove and re-connect one of your network drives in XP, it seems to behave itself from then on.

---

### Post by keith3232 on 2008-04-18
quirks is correct, it is a remote computer I'm trying to access. I was thinking along those lines too (Windows authentication issue). I checked the event viewer, but didn't find anything helpful there... only info icons refering to services starting and stopping (nothing in the security log).

---

### Post by keith3232 on 2008-04-18
I disconnected the mapped drive, and when I tried to reconnect I got the prompt for user name and password. This problem does not occur with the Suse server.

---

### Post by quirks on 2008-04-18
I have two questions:

In your first post, you said:
> When I try to access the Linux server from My Network Places or the mapped drive I am prompted for a password. Restarting Samba doesn't help, but if I reboot the Linux machine, everything works fine (until the next morning of coarse).
Are you saying that even when you enter the correct username/password when reconnecting the network drive, the mapping fails?

In your last post, you said:
> This problem does not occur with the Suse server.
Do you mean that when you map a network share on the Suse server in Windows XP, that you do not have such problems? Or do you mean that you can connect from the Suse server to the Ubuntu server?

Since you could not find any hints in the Event Logs, you might want to have a look at the Samba logs. They are in /var/log/samba.

quirks

---

### Post by bodhi.zazen on 2008-04-18
> **quirks said:**
> Are you saying that even when you enter the correct username/password when reconnecting the network drive, the mapping fails?

That is my question as well. Do you have a samba user on the Ubuntu server ? Are you using the samba user name and password to connect the share ?

---

### Post by keith3232 on 2008-04-18
I've tried all passwords (domain admin, root on Linux, admin on Linux, my user) and none were accepted. As for the second question, I meant that the Suse server grants access from XP, but both are true. I'll check the samba logs. I appreciate all the help!

---

### Post by keith3232 on 2008-04-18
I only have 2 accounts on the Linux machine (3 if you count root). Should I create a user for samba? Also, I need access without having to enter a user name and password.

---

### Post by keith3232 on 2008-04-18
I checked the samba log with my XP computer's name as the file name. This is what I see repeated (I assume once for every time I was rejected from accessing the server)
```

[2008/04/18 10:14:53, 0] auth/pampass.c:smb_pam_account(566)
  smb_pam_account: PAM: User "MyDomainName+" is NOT known to account management
[2008/04/18 10:14:53, 0] auth/pampass.c:smb_pam_accountcheck(780)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User MyDomainName+!
```

---

### Post by bodhi.zazen on 2008-04-18
> **keith3232 said:**
> I only have 2 accounts on the Linux machine (3 if you count root). Should I create a user for samba? Also, I need access without having to enter a user name and password.

Yes, you need to make a samba user on the linux (Ubuntu) server. It must be an existing user on the server who has permissions to access the shares on the server.

You do this with :

```
sudo smbpasswd -a username
```

where username = your samba user on the server.

You will be asked for a password.

Then enter that samba user and password in the windows dialog box when connecting to the server.

This all has to do with how samba is configured. Look at /etc/samba/smb.config if you want to change.

[https://help.ubuntu.com/community/SettingUpSamba#head-d2b25687b553d3737873748f613fb60558db7c4d](https://help.ubuntu.com/community/SettingUpSamba#head-d2b25687b553d3737873748f613fb60558db7c4d)

---

### Post by keith3232 on 2008-04-18
Thanks, I'll try that Monday. I had to reboot the server so people could get to the files they need.

---

### Post by BhRaviKiran on 2008-04-18
Hi,
    We have a Mono winform (version 1.2.4) application (server) running in Ubuntu 7.10 box. There is another application running on Windows XP box (client) . The two PCs are accessible to each other in the network.  We have installed the OpenSSL version 0.9.8e on Ubuntu box. 
We have also installed the net-SNMP-5.4.1 from source with openssl support.

[B]./configure --with-openssl
make
make all
make install[/B]

The applications in the two operating systems are supposed to communicate with each other. The application in the XP box has the SSL enabled and should communicate with the Ubuntu application where SSL is already enabled. 

When the client communicates with the server then we get the popup window titled "SSL Error" with description  "error:00000000::lib(0):func(0):reason(0).

We have also checked the "/etc/mono/config" configuration settings.
The symbolic links libssl.so and libcrypt.so are present as entries of dllmap and referring to the targets libssl.so.0.9.8 and libcrypt-2.6.1.so respectively. These libraries are already present in the /usr/lib directories. 
Another entry is dedicated to using the snmp that was installed in /usr/lib.

As a test whether SSL is enabled on the Ubuntu, we have tried the following command :
**openssl s_server -accept 50002.**

The client application was able to communicate with Ubuntu console at the particular port. The Ubuntu root console is able to receive the request from the client. So SSL is enabled at Ubuntu PC.

So why the mono winform application in the Ubuntu is unable to receive the client request when the SSL is turned on at either sides?

Thanks in advance.
Bh. Ravi Kiran

---

### Post by BhRaviKiran on 2008-04-18
Hi,
    We have a Mono winform (version 1.2.4) application (server) running in Ubuntu 7.10 box. There is another application running on Windows XP box (client) . The two PCs are accessible to each other in the network.  We have installed the OpenSSL version 0.9.8e on Ubuntu box. 
We have also installed the net-SNMP-5.4.1 from source with openssl support.

./configure --with-openssl
make
make all
make install

The applications in the two operating systems are supposed to communicate with each other. The application in the XP box has the SSL enabled and should communicate with the Ubuntu application where SSL is already enabled. 

When the client communicates with the server then we get the popup window titled "SSL Error" with description  "error:00000000::lib(0):func(0):reason(0).

We have also checked the "/etc/mono/config" configuration settings.
The symbolic links libssl.so and libcrypt.so are present as entries of dllmap and referring to the targets libssl.so.0.9.8 and libcrypt-2.6.1.so respectively. These libraries are already present in the /usr/lib directories. 
Another entry is dedicated to using the snmp that was installed in /usr/lib.

As a test whether SSL is enabled on the Ubuntu, we have tried the following command :
**openssl s_server -accept 50002.**

The client application was able to communicate with Ubuntu console at the particular port. The Ubuntu root console is able to receive the request from the client. So SSL is enabled at Ubuntu PC.

So why the mono winform application in the Ubuntu is unable to receive the client request when the SSL is turned on at either sides?

Thanks in advance.
Bh. Ravi Kiran

---

### Post by keith3232 on 2008-04-21
I added a samba user, and verified it had proper permissions. This didn't seem to help however. I entered the new user and password from the XP machine, and still couldn't access the server. I'm sure adding the samba user needed to be done, but what I really need is to access the server without entering in a user and password. Whatever is causing this issue is corrected when I reboot the Linux server. Does Ubuntu have a hard time dealing with inactivity?

---

### Post by stchman on 2008-04-21
> **keith3232 said:**
> Please forgive my ignorance, I'm very new to the world of Linux (although I must say it's been a pleasent struggle so far). Here is the senario... I have a server running Ubuntu gutsy, which logs into a Windows domain. The Linux box is a database (running postgreSQL and postGIS)/data storage server. I have everything setup correctly (or so I thought), all other machines on the domain can connect to the server and the databases. The problem is, every morning when I boot up my XP machine I get a message telling me that it couldn't connect to all mapped drives. When I try to access the Linux server from My Network Places or the mapped drive I am prompted for a password. Restarting Samba doesn't help, but if I reboot the Linux machine, everything works fine (until the next morning of coarse). This problem occurs on all the other Windows machines on the network. I have one more server setup with Suse Enterprise 9, and it can connect to the Ubuntu server. What really confuses me is the fact that I can connect to postgreSQL from all machines on the network, just not from Windows Explorer. I have know idea what I should do next, so I would certainly appreciate any advise.

Keith

You need to create a Samba account.  If you want the shares to boot up automatically then you will need to match the username and password of your XP login.  For example.

XP username:  joe
XP password:  password

Ubuntu server running Samba
sudo smbpasswd -a -L joe
you will be prompted to enter the password.

Your shares should auto connect when the XP machine boots up.

For each XP machine you need to do this.

---

### Post by keith3232 on 2008-04-22
That did it! Now that everyone has an account, they can all access it with no problem. Thanks again for helping!

Keith

---


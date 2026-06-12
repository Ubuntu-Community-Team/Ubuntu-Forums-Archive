---
title: "Access Samba Share From Windows"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by mcfly1204 on 2007-09-26
I have an old Compaq server with 6.06 on it added to my Windows AD.  My intentions for the server is to more or less be a file server for D2D backups.  I was hoping that by adding the server to the domain, I would be able to access a share on the Ubuntu server from a Windows box running our backup software.      I realize that I could setup the AD users as Samba users, but if an AD user password changes down the line, there will obviously be issues.  I was hoping to do something a little more clean.  Any thoughts?

-side note:  when I setup the share in Samba, I gave permission to the original Ubuntu user, and then one of the AD users.  Would the AD user need to be listed as Domain\username?

---

### Post by mcfly1204 on 2007-09-27
I should have titled this, "Cannot Access Samba Share Using Windows Authentication".  That is the problem that I am currently dealing with.  Windows users can log into the Ubuntu server without a problem, but they cannot access the Samba shares from a Windows system.  Any thoughts now?...

---

### Post by bigken on 2007-09-27
in the console/terminal type this 

sudo apt-get install samba

sudo smbpasswd -e yourname 
sudo smbpasswd -a yourname

---

### Post by bigken on 2007-09-27
go to system/administration shared folders to add your shares

---

### Post by mcfly1204 on 2007-09-27
I don't get your logic here, obviously I already have Samba installed, otherwise, why would I attempt to access Samba shares?  I already have the shares.  The shares were created and shared on the Ubuntu server.  However, when I am on a Windows system, I can see the shares, but am denied access to them.  So, my question is how can I grant access to AD users?

Also, I do not have a desktop installed.

---

### Post by mysticmatrix on 2007-09-27
> **mcfly1204 said:**
> I don't get your logic here, obviously I already have Samba installed, otherwise, why would I attempt to access Samba shares?  I already have the shares.  The shares were created and shared on the Ubuntu server.  However, when I am on a Windows system, I can see the shares, but am denied access to them.  So, my question is how can I grant access to AD users?

Also, I do not have a desktop installed.

You must create a SAMBA user that can access shares(Normal ubuntu username won't do)
That's why you've been suggested


```
sudo smbpasswd -e yourname
sudo smbpasswd -a yourname
```

For advance GUI, install GSAMBAD, found under Add/Remove

---

### Post by mcfly1204 on 2007-09-27
So you are saying there is no way to access Samba shares using Windows authentication?  I find that hard to believe given I can login to the Ubuntu system using Windows authentication.  I think you are missing that I am not concerned with Ubuntu users whatsoever.  

I can log in using Windows authentication, create a directory, change smb.conf to share that directory, but I cannot use the same Windows userID on a Windows system to access the share.

---

### Post by bigken on 2007-09-27
sudo smbpasswd -e yourname
sudo smbpasswd -a yourname 


well if you dont want to take the advice or at least try it thats up to you

---

### Post by Mr.Beast on 2007-09-27
> **bigken said:**
> sudo smbpasswd -e yourname
sudo smbpasswd -a yourname 


well if you dont want to take the advice or at least try it thats up to you

True, but perhaps a link to some more detailed Samba information would be more helpful?

If I knew where to find it, I'd link it here, and I'm also interested in what he's trying to do, I just don't have the answer either.

---

### Post by mcfly1204 on 2007-09-28
As I read more, I am thinking I need to look into the use of Winbind.  This should give me the ability to access samba shares via windows authentication.  This would eliminate the need to set up a sambapasswd, or a local account.  My intentions for this is to have windows users that can access the samba shares, but if they change their windows password, they can still access the samba shares.  My whole intention for this was to have a central repository for usernames/ passwords, in the form of a DC.  I will post more after some testing.

---

### Post by dmizer on 2007-09-28
edit:

deleted previous post because well, it was just totally wrong.

=======================================

here's some helpful information for creating a windows dc:
[http://www.docs.hp.com/en/B8725-90118/ch09s03.html](http://www.docs.hp.com/en/B8725-90118/ch09s03.html)

to create this, you're also going to have to install and configure kerberos as well as a properly configured /etc/nsswitch.conf

good luck with this, it's not something i've done yet.  let me know how it turns out.

---


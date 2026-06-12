---
title: "Please help me clear something out about SAMBA"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-04
Hi people,
What I would like to do is use my Ubuntu box on my LAN as a file server.
I have 6 winXP Pro machines and this Ubuntu box. All are networked with a switch and an ADSL Router for internet access.

Anyway,
what I would like to do, is to have my Ubuntu box share a directory to the network, for users on the winXP machines to access. 
I would also like to be able to create withing that folder subfolders with different user permissions. 

For example to create subfolders like /user01 and have an account with a password and username for accessing just that folder. Then /user02 etc etc

Now can I achieve this with SAMBA? and is the SWAT interface the best way to do this?

If yes, what is the list of packages required to install from synaptic?

Thanks for your help

---

### Post by schallstrom on 2007-09-04
You only need the samba package for a basic setup.

For a start I would read this: [https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88](https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88)

---

### Post by ROUBOS on 2007-09-04
Thanks for that.
Will look into it. SWAT looks like it's a good option but with a little reading I should be able to do without it.
Would anyone recommend SWAT?

Getting a little confused with users and all.
I only want to have the root user I got on my Ubuntu machine. User created on install.
Then I just want to create user names and passwords per shared folder. Is this what samba will do, or will I need to create user accounts for this linux box?

EDIT>> 
From the link you gave me "NOTE: the username used here should be a real user setup on your PC/Server. "

Does that mean that I need to create user accounts on my Ubuntu box for each home directory shared? What if I just want to have my account and create password protected subdirectories with different username access. For example :

user1 can access /home/Student01 directory
user2 can access /home/Stydent02 directory etc

---

### Post by schallstrom on 2007-09-05
I never used SWAT, so I can't say much about it. But generally it's not too hard to just configure the server through the config file as soon as you get used to it.

It's not the only possibility to create real system users for Samba authentication. You could even use something like MySQL, LDAP or Kerberos as an authentication backend. But that's far more work to set up, so the most basic Howtos use the system user for authentication (i.e. PAM).
If you are concerned about security, you could set the login shell for the Samba only users to /bin/false, so they can never login to the system.
```

# chsh -s /bin/false samba_only_user

```

---

### Post by ROUBOS on 2007-09-05
Hey there, after spending hours trying to set things up (noob here), I realized that SWAT is not worth bothering with.
So I did it manually and got things working. Needs alot of reading in order to understand how things work and the logic around it.
I love that about working with Linux..it's BRAIN FOOD :)

---

### Post by schallstrom on 2007-09-05
Glad to hear that you are making progress.

The more you experiment with setting up different servers and stuff and playing around with the configurations, the easier it will get.

---


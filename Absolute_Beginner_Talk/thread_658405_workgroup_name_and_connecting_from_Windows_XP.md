---
title: "workgroup name and connecting from Windows XP"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by kavoura on 2008-01-04
I am using Ubuntu 7.10 and trying to network with a Windows XP PC. In Windows and another Linux PC I have set the workgroup name to Forest, but when I enabled networking in Ubuntu it seems to have defaulted to Mshome. How do I change it to Forest?
Also, from the Windows PC I can see the Ubuntu PC on Mshome, but I cannot connect to it. I get a window asking for username and password. I enter the ones used in Ubuntu but it will not connect. I can connect to Windows from Ubuntu though and copy files, etc. 
So how can I connect to Ubuntu from Windows?

---

### Post by njparton on 2008-01-04
Look in the administration menu for networking - under there you can set the workgroup name if you dig around a little.

To access ubuntu from windows you'll have to share specific folders using samba. This will need installing and configuring. Seach these forums, there's tonnes of info.

For accessing windows from ubuntu you'll need to mount the NTFS hard drive using NTFS-3g or CIFS (latter similar to samba).  Again search for how tos.

---

### Post by kavoura on 2008-01-04
In the Administration menu there are two items related to Networking, "Network" and "Network Tools". I looked thoroughly in those programs and there is nothing there to set the workgroup name. Also there is a program called "Network Settings" under Applications/Other, but that has nothing to rename the workgroup.
There surely must be a setting in Ubuntu to specify the workgroup, but where is it?
I have already shared folders in Ubuntu with Samba. But in Windows to connect to the Ubuntu PC it requires a username and password. I tried my Ubuntu username and password, which is the same as what I use in Windows, but it will not work.

---

### Post by kavoura on 2008-01-04
> **njparton said:**
> For accessing windows from ubuntu you'll need to mount the NTFS hard drive using NTFS-3g or CIFS (latter similar to samba).  Again search for how tos.

Networking makes this irrelevant. It does not matter what filesystem is on the other PC, if the other PC is sharing a directory it can be accessed by any PC on the network with rights to access that PC. I have already accessed a shared drive on the Windows PC without any need to specifically mount it.

---

### Post by njparton on 2008-01-04
Oh yes there is...

System > adminstration > network > General Tab - domain name (or "workgroup") is one of the fields there.

You'll need to install and configure samba to access files from windows, that includes creating a samba password which for you currently won't exist hence your problem.

---

### Post by njparton on 2008-01-04
```

sudo apt-get install samba smbfs
sudo smbpasswd -a *username*

```

Then right click on folders to share or directly edit the config file:

```

sudo gedit /etc/samba/smb.conf

```

Then restart samba daemon:

```
sudo /etc/init.d/samba restart
```

This will also allow you to mount a CIFS share via fstab to access windows from ubuntu. Search for a how to. Off to rest my weary head now...

---

### Post by steve-shinn on 2008-01-04
Instructions for setting up user accounts :-

1.1 Starting samba and setting up user accounts

Let us fire up samba for the first time. Type:

Code:
sudo /etc/init.d/samba start
There shouldn't be any errors - if you are presented with an error message make sure everything is correct (search for typos and/or invalid paths).

Time to add yourself as an samba user.

NOTE: You will be asked for a password - make sure you use the same as you use for login!

Code:
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!

---

### Post by kavoura on 2008-01-04
I found a howto at 
and edited my smb.conf file to change the workgroup name. I also added my username as a samba user with the same password. 
Then I restarted samba.
Now from the Windows PC I can see the Ubuntu PC in the correct workgroup, but  could not access it. Also from another PC on the network, running Mandriva, that too can see the Ubuntu PC but could not access it.
I can access the Mandriva PC okay, it asks me for a password, which I enter and it gives me access. I can access the Windows PC okay without any password.
Anyway, I then decided to reedit the smb.conf file and look for errors. I uncommented out the line "guest account = nobody" and now I can access the Ubuntu PC from the other PCs.

For all its ease of use, Ubuntu is really good, except for networking which seems to be something the developers probably believe no beginner or basic user will ever need to worry about.

---

### Post by rh10023 on 2008-01-05
I have just made the plunge to Ubuntu.  (I have been a Fedora user for a few years.)  I am having a dickens of a time trying to get Samba to work.  I have done the smbpasswd -a and smbpasswd -e.  I have encrypt passwords set to yes.  But I still get the following error message on my XP Pro laptop.

\\fileserver\fileshare is not accessible. You might not have persmission to use this network resource. Contact the adminstrator of this server to find out if you have access permissions.

Incorrect function.


Tried looking all over the forums for some Ubuntu specific tips and tricks for samba, but can't find one that will fix this problem.  I have always been able to connect to samba with this computer before when my server was Fedora.  So I know there that isn't anything wrong with the laptop.

Anyone been able to get an XP Pro machine to connect to a samba share on a Ubuntu machine?  If so, what steps did you take to make it work?

---

### Post by oldsmobile_mike on 2008-01-06
Somebody needs to write a faq or guide to this, 'cause it's not easy.  But as previous people posted, to be able to connect from a Windows machine to a Ubuntu machine, you have to:

Download Samba (will be downloaded automatically if you right-click on a folder and try to share it)
Change your workgroup name - default is mshome, which I doubt anyone uses.  To do this edit the smb.conf file in etc/samba (will need root permission, such as by "gksudo nautilus" to be able to save your changes).  Also, while you're there, un-comment out the line that says "guest account = nobody".

After this, you need to add a Samba password: "sudo smbpasswd -a username" at the command prompt.

Finally, select a folder to share on your Ubuntu machine.

Done, tested, and working.  :-)

Oh, btw - I saw someone get kind of argumentative that on the General tab of Network Settings there was a way to change your workgroup.  Nope, sorry, there isn't.  I'm looking right the general tab.  It has to be done from the smb.conf file.  :-(

---

### Post by saj0577 on 2008-01-06
The option on the general tab is domain not workgroup which is different.


Saj

---

### Post by kavoura on 2008-01-07
Yes, setting up samba to allow WinXP to access Ubuntu is difficult. 
One other thing I did which may or may not have been necessary, in the smb.conf file, was to change
encrypt passwords = true
to
null passwords = true

and then I could log into Ubuntu without it asking me for a password. Prior to that, no matter what I did in setting up the samba user, WinXP could not log into Ubuntu as it was being asked for a username and password, and despite having set these in Ubuntu for samba, it would not work. After setting the null passwords bit I could then log in. Note that I had the same problem logging into Ubuntu from a PC running Mandriva 2008, and after fixing the smb.conf file with all the necessary changes, both Mandriva and WinXP could log into Ubuntu.
Canonical really should make networking a lot easier in Ubuntu. Most things in Ubuntu are easier than in other Linux distros, but networking seems to be something they consider most users do not need to know about. When I was using Xandros that worked perfectly with networking with almost zero configuration required. But I am using Ubuntu now because of problems with display drivers in Xandros. So far Ubuntu has been very stable and reliable.

---

### Post by njparton on 2008-01-07
> **kavoura said:**
> Yes, setting up samba to allow WinXP to access Ubuntu is difficult... 


I found it remarkably easy with both XP and Vista.  I've even got it set up to deny and allow specific hosts for specific shares without any problems.

I just took the time to read up about samba before I started :)  Loads of good information out there.

In general allowing guest connections and plain passwords isn't very secure unless you're happy with the security of your network (and it's users).

---


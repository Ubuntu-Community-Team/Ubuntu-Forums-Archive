---
title: "File Sharing help, why is this hard?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by adwatkin19 on 2007-08-14
Right in my house we are all big techies, and we have 4 PC's and 2 laptop's.

We have three of the PC's running Windows XP, one of the PC's is running gibbeon

one laptop is on feisty and the other laptop is on Mac OSX

Basically i want to share files between them all and can i do it, can i heck. 

I have tried browsing the network, but when i do that i get asked for a user name and password. i have never put any sort of authentication on it. I can only see MSHOME but cant get in to see what is in the MS HOME. 

i have tried connecting to the IP address, but nothing seems to happen. is there anywhere where i can get a nice simple to follow guide because this is stressing me out big time. i only want to share a few files across the network, nothing major. 

thanks for any help, please ask questions you need to. 

Adwatkin19

---

### Post by mohnkern on 2007-08-14
Samba and sambfs should give you want you need.  See [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Hospadar on 2007-08-14
If you just want to transfer files (if you don't want a shared drive) you could use ftp or ssh (you'll have to install the server modules on linux, probably on osx also) and then use a tool like gFTP

---

### Post by adwatkin19 on 2007-08-14
Hi, thanks for the replys

i have got Samba installed on the linux machines, and i can now see one of the pc's even though there are two on and have shared folders. 

The two windows pc's cannot see the linux machines though

on both the linux machines i have set up a folder that is shared, but nothing seems to be happening as a result, 

thanks for the help so far. 

Adwatkin19

---

### Post by yellowband on 2007-08-14
hi adwatkin

have you tinkered with the samba config file yet?

sudo vi /etc/samba/smb.conf

look for two options:
browsable = yes
writable = yes

I have had some frustrating times with samba, basically i found the easiest way to share with it is to share your home directory (or a folder in  your home directory).

if you want a little more security you could add all your buddies as users on your linux computer, then change the samba config to:

security = user;

this will force whoever is trying to log into the linux box via samba to supply their user/assword.

Oh one more thing, dont bother tinkering with samba until you have a solid TCP/IP network working.  open up your terminal and ping the various hosts on your network by name and ip address.

---

### Post by Jerry N on 2007-08-14
ME TO!  I can easily file share between multiple XP machines and Win98 machines and I can get UBUNTU (7.04) to read and write files on the XP machines BUT I have not yet been able to share files and folders on the UBUNTU machine with XP machines.  I admit I have only spent a few hours on this but the year is 2007 and I can't see why there needs to be command line incantations and .conf file manipulations for something that has become as common as file sharing.  The folks that created Freespire 2 must think that too because setting up file sharing between Freespire 2 (UBUNTU 7.04 based) and XP computers is as nearly trivial as it could be.  

I can't try file sharing between UBUNTU and Freespire 2 because it is the same computer!
BTW, Freespire 2 looked a bit grubby to me initially but after some tune-up it is starting to look pretty good.  

Jerry

My reasons for looking at LINUX are (1) determine if LINUX is a suitable OS for me at such time that XP becomes unsupportable (2) determine if I can recommend LINUX when asked by friends and associates that are only interested in a computer appliance that works, not a technical challenge.

---

### Post by yellowband on 2007-08-14
i forgot to mention you need to add users to samba.

first create any users you want on your unix system.  then issue the command

sudo smbpasswd -a <name of user you added>

---

### Post by Armman on 2007-08-14
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by yellowband on 2007-08-14
was just about to post that Arrman


long story short, right click on the folder you want to share from ubuntu and click "share folder".  use the samba option at the following prompt.  


Jerry: i agree that .conf files and other configurations can be annoying and cumbersome, especially when you are used to doing things a different way.  I think its about flexability and scalability though.  samba can be used for simple home network projects like this, to huge domian controller setups, . I guess they need a clever programmer to make a GUI front end for your purposes.

and in fact there is one!  check out SWAT.  its a web-based administration for samba.  its pretty awesome, and not too difficult to set up.  i think there is a how-to at [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by notwen on 2007-08-14
You may want to consider NFS, but it would be alot easier if you guys created a share folder on one specific PC and then mount that one shared drive on the remaining PCs.  Depending on what you're wanting to do w/ these shared folders/files, NFS is alot more usable.  I use NFS to to play my media(located on my PC) on my laptop w/o ever having to take up HDD space on the laptop.  I've never used NFS over a multi-OS network, but it may be worth a look. Good luck w/ your file-sharing issues. =]

---

### Post by adwatkin19 on 2007-08-14
right, i have managed to get all the computers to see each other.

But this is the problem now:

all machines can look at the windows xp shared folders,

but none of the machines can access the linux shared folders without a username and password, but i dont want this to happen, is there anyway i could just disable this username and password?

thanks alot for any help

adwatkin19

---

### Post by Salpiche on 2007-08-14
try using a really short password then, if it is in a secure network you could get away with using a one character passwd.

---

### Post by ugm6hr on 2007-08-14
> **adwatkin19 said:**
> but none of the machines can access the linux shared folders without a username and password, but i dont want this to happen, is there anyway i could just disable this username and password?

Yes.  The solution is here:
[http://ubuntuforums.org/showpost.php?p=3036386&postcount=3](http://ubuntuforums.org/showpost.php?p=3036386&postcount=3)

It's the **security=share** you need to add (you should have done the rest already).  That removes the samba password on the Ubuntu box.

---

### Post by adwatkin19 on 2007-08-14
> **ugm6hr said:**
> Yes.  The solution is here:
[http://ubuntuforums.org/showpost.php?p=3036386&postcount=3](http://ubuntuforums.org/showpost.php?p=3036386&postcount=3)

It's the **security=share** you need to add (you should have done the rest already).  That removes the samba password on the Ubuntu box.


that was exactly what i was looking for as the last piece in the puzzle 

thanks to everyone who contributed, this really is an awesome community

thanks again

adwatkin19

---

### Post by ugm6hr on 2007-08-14
> **adwatkin19 said:**
> thanks to everyone who contributed, this really is an awesome community


All the information is out there (and free) to do this kind of thing.  Difficulty is knowing:
a. where to look... and
b. what to look for.

Thankfully, someone here will always know the answers to both :)

---


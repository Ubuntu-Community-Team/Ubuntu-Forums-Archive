---
title: "[SOLVED] Network to XP pc possible?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Daveg4otu on 2008-03-29
Have two PC's (mine & hers)....Mine has Win XP + Ubuntu. -Hers  is  Win XP.

Under XP  they are networked via the Netgear DG 834  router.

Is it possible for me to set up the same network   Ubuntu(me) to XP (her) ..? If so - how?

Both XP installs are FAT32....

Any advice welcome.

---

### Post by srirambond007 on 2008-03-29
Yes ofcourse ...
to do that u have to install Samba . by default its not installed ...

To install: sudo apt-get install samba

Once the server is install, issue the following command:

Code:

sudo gedit /etc/samba/smb.conf

Make the following changes:

Code:

 workgroup = WORKGROUP

underneath it, add

netbios name = name_of_your_server (no spaces)

For example:

Code:

netbios name = ram_smb_server

Make sure "security" is set to "user".

Scroll down until you see "[homes]", set:
Code:

browseable = yes
writable = yes

Then save the changes.


Finally, create a SMB user, make sure this account exists on your Ubuntu Linux.

Code:

sudo smbpasswd -a `test`

and set your password

OKAY, you are finished configuring Samba on your Ubuntu Linux.

------------------------------------------------------------------------------------------------
Winblowz
------------------------------------------------------------------------------------------------

There are two ways to access it:

Method 1:
My network places > Entire Network > My Windows Network > Workgroup

Method 2:
in the address barm type in "\\[whatever you named the Samba server]". From my example above, I used "\\ram_smb_server\".


You should see a folder call "home", click on it, and it will ask you for your username and password, enter your Ubuntu Login 

Name and whatever you choose for the password when you used command "smbpasswd". You should be able to take it from here.

Keep in mind that you are sharing, /home/[login name]/*

------------------------------------------------------------------------------------------------
Linux
------------------------------------------------------------------------------------------------

Install smbfs:

Code:

sudo apt-get install smbfs
mkdir Network
sudo mount -t smbfs -o username=[network user],password=[network pass],uid=`test`,gid=`test`,fmask=000,dmask=000  //[whatever 

you named the Samba server]/[network user] /home/`test`/Network

Example:

sudo mount -t smbfs -o username=ram,password=test,uid=`test`,gid=`test`,fmask=000,dmask=000  

//ram_smb_server/ram/home/`test`/Network


All the best

---

### Post by Daveg4otu on 2008-03-29
Thanks -will give that a try later today.

---


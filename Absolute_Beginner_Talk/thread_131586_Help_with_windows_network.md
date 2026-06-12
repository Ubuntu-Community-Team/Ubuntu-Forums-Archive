---
title: "Help with windows network"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by BitTorrentBuddha on 2006-02-16
Hey, I've got samba installed, but when I try and access my ubuntu files from my windows pc or vice versa I'm prompted for a password and username, I need to know which combination of username/password I need to use to access each, thanks.

---

### Post by Iowan on 2006-02-16
Seeing no other responses, I'll throw in my nickel's worth (2 cents after inflation and taxes):  My guess (stress *guess*) is that with Samba as the intermediary, it's the Samba user/passwork being sought.

---

### Post by tbg58 on 2006-02-16
When you set up Samba there are several requirements you need in order for Windows clients to to have access to your share.
First, each user name that will be accessing Samba must have both a named account on your Ubuntu box (which you can set up using System, Administration, Users and Groups).
Second, you'll need to have Samba set up.  I will assume you have it installed and you have selected a file system or directory to share.
Third, each user account must also be set up as a Samba account.  You can set this up using the command smbpasswd.  Use smbpasswd --help for more information.
Fourth, you need to have the proper group permissions set up in the directory you've shared.  The easiest way to do this is to set up a group for all your samba users.
Once the group is set up, add all the accounts that you want to have access to the share to that group.
Next, run chgrp for the directory you are sharing so that the group for the Samba share is your samba users group.
Fifth, the directory needs to have the proper permissions set.  For a home network, if you will chmod 775 [directory name] that will probably be all you need.

In review:
1.  User name on Ubuntu OS.
2.  Samba installed and smbd running (use ps -A to check -- you should have one or more smbd processes).
3.  Samba user account set up
4.  Samba group set up with permissions to the share.
5.  File system permissions set.

For more information, you can download the Open Book from Bruce Perens' series on this page at the Prentiss Hall Publisher web site.
[http://www.phptr.com/promotions/promotion.asp?promo=1484&redir=1&rl=1](http://www.phptr.com/promotions/promotion.asp?promo=1484&redir=1&rl=1)
The Samba Howto and Reference Guide is the fifth book down in the right hand column.
While you're there, I would take the time to download every open book that they have -- there are a bunch, but well worth the time it takes to download them.
Not every bit in every chapter applies to Ubuntu, but there is enough good information there for you to become expert enough on Samba to make it tap dance for you.

Hope this helps!

Kindest regards,

Pastor Rob (The Bald Guy)

---

### Post by BitTorrentBuddha on 2006-02-16
how do I set permissions for groups?

---

### Post by tbg58 on 2006-02-17
When you do an ls -l the permissions are listed like this:
-rwxrwxrwx  (username) (groupname)  filesize  ModDate&Time filename

The first block has three groups of rwx (read, write, execute)
The first rwx is the permission list for (username)
The second rwx is the permission list for (groupname)
The final rwx is the permission list for (other -- same as Everyone).

You user chmod to change the permissions.  You can man chmod to get the particulars.  Some folks like to use the +r +w -x method, but I find it's easier to remember the syntax of the numberic method.
For each rwx group, each permission has a numeric value:
r=4  (read)
w=2 (write)
x=1  (execute)

If you can remember these three numbers you've got it licked.
The numeric values add together for each group, e.g.
4+2+1=7=rwx
4+0+1=5=r-x
4+2+0=6=rw-

Say you want your user and group owner to be able to read and write but not execute and you want everyone else to have no permissions at all.
read=r=4
write=w=2
4+2=6
So for this permission you can do a chmod 660 (filename) and presto, you've given read and write permissions.

A general rule of thumb -- for a home server 775 permissions will do just about everything you need.  Your user, your group both have all permissions in the directory.  Guests can read and execute but not write -- they can look, but not touch.

Hope this helps.

Pastor Rob (the bald guy)

---

### Post by BitTorrentBuddha on 2006-02-17
ok, That all worked, now all I need to find out is what password do I put in to access the files on the windows computer from the ubuntu thing, it's not the same as the one as the windows accessing ubuntu password.

---

### Post by BitTorrentBuddha on 2006-02-17
how do I set up a password or find whatever password already exists to access windows files? or is this impossible from ubuntu?

---

### Post by BitTorrentBuddha on 2006-02-18
...bump :???:

---

### Post by alamba on 2006-02-18
smbpasswd

A

---

### Post by BitTorrentBuddha on 2006-02-18
...?

---

### Post by knalle on 2006-02-18
man smbpasswd

---

### Post by janclodvandam on 2006-02-18
As you can see by the number of my posts, i AM the absolut begginer.I have the same problem with the lan between an ubuntu pc and a windows pc.
From the windows pc i can see now the ubuntu but i cant see the folders that i'm sharing.And it requires password.I used smbpasswd but it doesnt work.Any ideas?

---

### Post by alamba on 2006-02-19
Samba requires a username and password to access a share. You need to define the share and the users allowed to access it in smb.conf.Then using smbpasswd you can create a username and a password for that username.

Suggest you type man smbpasswd on your terminal and read up.

A

---

### Post by tbg58 on 2006-02-19
Okay, if I understand correctly, you want to access a drive on a Windows host from Ubuntu.

First, create a new Windows user on the Windows box with the permissions you want.
Create a share by sharing a file.  There are several ways to do this, but for now we'll just assume you want to use share permissions.  If you're using an AD domain controller then you can use user permissions, but we'll assume that for now you know how to share a folder on the Windows box.

You have a share and you have an account and password to use.

smbfs should be already installed on the Ubuntu box.  If it's not, then
sudo apt-get install smbfs

Once it's installed, then you use

(the following is on one line)
mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword


Notes:
//servername/sharename refers to Windows box and the name of the share.

/mountdirectory refers to any directory on the Ubuntu box you want to use as a mount point -- The user who runs the command must have write rights to it. 

I thought that smbfs was already included in the kernel, but I had to apt-get it for my Breezy box.

Hope this helps,

Pastor Rob (the bald guy)

---

### Post by Cephyr on 2006-02-22
Hey! I had the exact same problem. All of the sudden, whenever I opened Network Servers it wanted a username and password!

I fired up smbpasswd, and it said for some reason my account was disabled. So, I did this:

sudo smbpasswd -e (username)

...then typed in a new password, and entered in at Network Servers and everything worked great. Thanks!

---

### Post by BitTorrentBuddha on 2006-02-23
ok, I think the problem may be that I'm using the wrong domain name or something, because I can't get this working, the domain name I keep using is MSHOME [the one there by default] does this need to be changed and if so where can I find the correct domain? [note: I have two instances of smb.conf, one in /etc/samba and the other in /usr/share/samba. They differ as follows, workgroups read MSHOME and DEBIAN_FANS respectively, encrypt passwords = true and no respectively, only /etc/samba/smb.conf contains the cups printing section, the /etc/samba instance includes the extra line wins support = no, and they contain different parameters for writable (yes - no respectively)]

---

### Post by dvarsam on 2006-02-24
Sometimes, when you have problems & you can NOT solve them, it is nice to make a search on some other "Samba" articles.

I do NOT know if by reading them, you are going to get your case solved, but you'll master your Samba more...

Article: 122570
Article: 124541

Also, it is a good idea, when you make a Post, instead of a Title, like:

"Please Help", or
"What is this" or
"Help with windows network" (your case)

Better type:

"Help solve Samba problem"

Then anybody who wants to find other related articles, could just make a search on "Samba" in this Forum's Database.

Thanks.

---


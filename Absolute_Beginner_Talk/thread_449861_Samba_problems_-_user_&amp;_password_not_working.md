---
title: "Samba problems - user &amp; password not working?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by kexodusc on 2007-05-20
Having a bit of a problem here.
I followed a few of the Samba guides and have made some good progress towards getting my laptop with Windows XP (wireless) and my Ubuntu machine up and running on my network.

The Ubuntu box can see the XP box on the network, access the shared files, etc.
The XP box can see the Ubuntu machine, but when I try and access the shared files, I get a prompt for the user name and password.

So I enter those, and nothing.  Not letting me in.  I'm stumped.  
Anyone got any ideas where I'm going wrong?

---

### Post by dolphin_oracle on 2007-05-20
My initial guess is that you need to setup another account on ubuntu and samba.  add a new user for the remote xp machine in ubuntu, with its own username and password.  then, under the terminal, make a new samba user with the same username and password you just created.

smbpasswd -a username

Use this account to log in when xp asks for a password.

Good luck!

---

### Post by Iokua on 2007-05-20
dolphin_oracle is correct, but you don't need to create another Ubuntu user if you don't want to. You can use your current account and just create a samba user with a password different from your login.

---

### Post by kexodusc on 2007-05-20
> **Iokua said:**
> dolphin_oracle is correct, but you don't need to create another Ubuntu user if you don't want to. You can use your current account and just create a samba user with a password different from your login.

Thanks guys, I've already tried creating the samba users and passwords.  Their enabled.  When I type that same info into the prompt in Windows XP, it just doesn't work.

---

### Post by dolphin_oracle on 2007-05-20
double check that the user you created has the proper permissions for the folder.  For instance, my desktop user is part of a group called family.  I set all my users that log in through samba to belong to the family group.  Then I set the shared folder to be accessible by group family.

as an alternative, you could set your share to public and see if you can get in that way.

---

### Post by kexodusc on 2007-05-20
> **dolphin_oracle said:**
> double check that the user you created has the proper permissions for the folder.  For instance, my desktop user is part of a group called family.  I set all my users that log in through samba to belong to the family group.  Then I set the shared folder to be accessible by group family.

as an alternative, you could set your share to public and see if you can get in that way.

Thanks, checked and verified shares are set to "public", "available", and "browsable".
Tried yet another user and password, still not connecting though.  It doesn't appear to be accepting the password or user names I try.

---

### Post by dolphin_oracle on 2007-05-20
I've only got one more thought, also related to permissions.  under nautilus, right click on the folder you are sharing and choose properties.  Check the permissions tab and see what kind of rights your ubuntu users have to the folder.  Unless your samba user matches your ubuntu user, I believe you'll need to make sure that the Others area is set to at least access.

Good luck.  If this isn't the problem, someone with more chops than me needs to chime in!

---

### Post by djchandler on 2007-05-20
> **kexodusc said:**
> Having a bit of a problem here.
I followed a few of the Samba guides and have made some good progress towards getting my laptop with Windows XP (wireless) and my Ubuntu machine up and running on my network.

The Ubuntu box can see the XP box on the network, access the shared files, etc.
The XP box can see the Ubuntu machine, but when I try and access the shared files, I get a prompt for the user name and password.

So I enter those, and nothing.  Not letting me in.  I'm stumped.  
Anyone got any ideas where I'm going wrong?
Adapt this smb.conf file and see if it works
CAUTION - NO PASSWORD OR ACCOUNTS NECESSARY TO SHARE DIRECTORY
ON YOUR LINUX BOX

Example follows:

# start samba configuration file instructions
# rename to smb.conf and copy to  the /etc/samba/ directory
# change Your* to actual names you are using - will set 
# wide-open samba share - no passwords necessary on the lan to
# get to shared linux directory
# sorry, using tcp/ip printing through JetDirect on LaserJet
# no host computer for printer - cups works great with this

# Start actual conf file with [global] label



[global]

workgroup = YourWorkgroup
# if part of a domain should be
# domain = YourDomain - the uncommented lines (no # in front)
# will just set you up for a small local workgroup  domain not
# necessary unless actually part of domain - very simplest
# type of Windows share illustrated here - NO SECURITY!
netbios name = YourLinuxBox
# name of your computer for Windows network

server string = YourServer
# Further ID of the netbios server interface

security = share

local master = yes

os level = 35

wins support = no


[Share]

comment = Shared Folder

# check path for shared folder(s)

path = /YourFolder

public = yes

writable = yes

guest ok = yes

available = yes

browseable = yes

oplocks = no

level2 oplocks = no

inherit permissions = yes

create mask = 0775

directory mask = 0775



#End file

---

### Post by esoterica on 2007-05-20
Go through these steps and it should work just fine for you

[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

[http://blogs.zdnet.com/Bott/?p=236](http://blogs.zdnet.com/Bott/?p=236)

---

### Post by djchandler on 2007-05-20
> **djchandler said:**
> Adapt this smb.conf file and see if it works
CAUTION - NO PASSWORD OR ACCOUNTS NECESSARY TO SHARE DIRECTORY
ON YOUR LINUX BOX

Example follows:

# start samba configuration file instructions
# rename to smb.conf and copy to  the /etc/samba/ directory
# change Your* to actual names you are using - will set 
# wide-open samba share - no passwords necessary on the lan to
# get to shared linux directory
# sorry, using tcp/ip printing through JetDirect on LaserJet
# no host computer for printer - cups works great with this

# Start actual conf file with [global] label



[global]

workgroup = YourWorkgroup
# if part of a domain should be
# domain = YourDomain - the uncommented lines (no # in front)
# will just set you up for a small local workgroup  domain not
# necessary unless actually part of domain - very simplest
# type of Windows share illustrated here - NO SECURITY!
netbios name = YourLinuxBox
# name of your computer for Windows network

server string = YourServer
# Further ID of the netbios server interface

security = share

local master = yes

os level = 35

wins support = no


[Share]

comment = Shared Folder

# check path for shared folder(s)

path = /YourFolder

public = yes

writable = yes

guest ok = yes

available = yes

browseable = yes

oplocks = no

level2 oplocks = no

inherit permissions = yes

create mask = 0775

directory mask = 0775



#End file
One more thing - set permissions on shared folder to at least read.
Group can be account current user is logged in under.

It works! I'm sitting behind a hardware NAT firewall with prettty high
security settings. Hence my lack of interest in security for this share/

---

### Post by kexodusc on 2007-05-21
> **esoterica said:**
> Go through these steps and it should work just fine for you

[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

[http://blogs.zdnet.com/Bott/?p=236](http://blogs.zdnet.com/Bott/?p=236)


Hi, and thanks for the link to the guide.  Hadn't tried that particular one.

Unfortunately I'm left with the same problem.  The XP laptop can see the Ubuntu box on the network, prompts for a user name/password to access, but they don't work.

Unfortunately, I can't operate this network without usernames and passwords.  

I'm really stumped here, wonder if it could be a setting on the XP laptop?  BTW, when I run XP on my main PC, there's no problems with the network.  
I dunno, the file system is Fat32 on the laptop, shot in the dark, but I think that has fewer sharing abilities than NTFS, any chance that's holding me back?

---

### Post by dolphin_oracle on 2007-05-21
I don't think the FAT filesystem is the issue.  I'm personally at a loss at this point.

from a terminal, can you navigate to the parent folder of your shared drive and run this command and post the output

$ ls -l

the -l will show us all the permissions on the shared folder.

---

### Post by lazyart on 2007-05-21
What I *just* did because I had shared a folder yesterday but couldn't get into it:```
sudo smbpasswd -e *username*
```

This had the effect of enabling the *username* account which is already used in Ubuntu to have access remotely.  It first asked for the root password (because i had to use SUDO) then it asked for new SMB password, which I set to the same as my own.

Then I went to my windows box, browsed to my ubuntu machine, found the folder, and this time it accepted my username and password.  So I don't think it's enough just to add the user (smbpasswd -a *username*) but you might have to enable them as well.

Hope this helps.

---

### Post by kexodusc on 2007-05-21
> **dolphin_oracle said:**
> I don't think the FAT filesystem is the issue.  I'm personally at a loss at this point.

from a terminal, can you navigate to the parent folder of your shared drive and run this command and post the output

$ ls -l

the -l will show us all the permissions on the shared folder.

Here's the output from the folder:

total 128
-rw-r--r-- 1 ken ken 124928 2007-05-21 14:35 Proposed Paid Security Info.xls

---

### Post by kexodusc on 2007-05-21
> **lazyart said:**
> What I *just* did because I had shared a folder yesterday but couldn't get into it:```
sudo smbpasswd -e *username*
```

This had the effect of enabling the *username* account which is already used in Ubuntu to have access remotely.  It first asked for the root password (because i had to use SUDO) then it asked for new SMB password, which I set to the same as my own.

Then I went to my windows box, browsed to my ubuntu machine, found the folder, and this time it accepted my username and password.  So I don't think it's enough just to add the user (smbpasswd -a *username*) but you might have to enable them as well.

Hope this helps.

Thanks, been trying that as well, all the users are enabled.

---

### Post by dolphin_oracle on 2007-05-21
Are you by any chance trying to share your home folder?  Ubuntu doesn't like that very much, and can lead to all kinds of wonky behavior. 

Was the output you posted above run from inside shared folder?  If so, we need to go one level up and rerun the "ls- l" command.

to go back a level, 

$ cd ..

---

### Post by kexodusc on 2007-05-21
> **dolphin_oracle said:**
> Are you by any chance trying to share your home folder?  Ubuntu doesn't like that very much, and can lead to all kinds of wonky behavior. 

Was the output you posted above run from inside shared folder?  If so, we need to go one level up and rerun the "ls- l" command.

to go back a level, 

$ cd ..

No, this is a folder inside my home folder (not in my user name folder though) simply titled "samba" for lack of creativity on my part.  The output was from in the "Samba" folder.

 Here's the new output, up a level as you requested.  Thanks for your help, btw.

drwxrwxrwx 49 ken  ken   4096 2007-05-21 15:23 ken
drwx------  2 root root 16384 2007-04-21 06:05 lost+found
drwxr-xr-x  2 root root  4096 2007-04-22 15:10 Recycled
drwxrwxrwx  2 root root  4096 2007-05-21 14:35 samba
drwxr-xr-x  2 1003 1004  4096 2007-05-21 07:43 steph

---

### Post by dolphin_oracle on 2007-05-21
the folder owner and group are both set to root.  Perhaps you should change this so that the group and/or owner is one of your user accounts.  The permissions are set so that the world should be able to see it but maybe the root group is different (I'm guessing some here). 

You should be able to change the owner by launching a root nautilus

$ gksudo nautilus

Then adjust the properties on the folder.  Make sure to specify a group and owner thats not root.

And your welcome.  :)  I just hope we get this working...

---

### Post by kexodusc on 2007-05-21
> **dolphin_oracle said:**
> the folder owner and group are both set to root.  Perhaps you should change this so that the group and/or owner is one of your user accounts.  The permissions are set so that the world should be able to see it but maybe the root group is different (I'm guessing some here). 

You should be able to change the owner by launching a root nautilus

$ gksudo nautilus

Then adjust the properties on the folder.  Make sure to specify a group and owner thats not root.

And your welcome.  :)  I just hope we get this working...

Okay, I changed the owner...not sure I understand why, but it hasn't changed anything.  I trust I should have the same owner settings for all shared folders?

---

### Post by dolphin_oracle on 2007-05-21
To be honest, it was just a shot.  A lot of my trouble when I set mine up came from permission and owner issues.    With the permissions set the way you have them (drwxrwxrwx), it shouldn't have (and didn't) matter.

I'm afraid I'm at the end of my (limited) knowledge here.   Sorry.

---

### Post by kexodusc on 2007-05-22
Well, when I went back into smb.conf and set up "security = share" instead of security = user I can access my Ubuntu box shares.

Weird, that tells me there's a smb.conf setting I'm overlooking or I'm typing in the user and/or password info wrong every single time (highly unlikely).
Guess I'll keep tinkering.

Let me ask this.  How badly am I exposed if I have "security = share"?
Can anyone within the range of my router access those shared files?  Would they need to know the name of workgroup at least (it's not the default XP name)?

---

### Post by dolphin_oracle on 2007-05-22
These leads back to the user accounts we started tinkering with.  I've been playing with my systems here, and with security=share set up, the only real security my folder had were the system permissions.

just a quick refresher:  the samba_user account must have the same login name and password as a valid system_user account.  These are all case sensitive.  The security layers are the samba permissions (public, writable, etc...) and then the system permissions (-rwx).  

I'm really at a loss here, and I can't seem to replicate your issue.  If in your tinkering you figure out the issue, please post your solution here.

---

### Post by djchandler on 2007-05-22
> **kexodusc said:**
> Well, when I went back into smb.conf and set up "security = share" instead of security = user I can access my Ubuntu box shares.

Weird, that tells me there's a smb.conf setting I'm overlooking or I'm typing in the user and/or password info wrong every single time (highly unlikely).
Guess I'll keep tinkering.

Let me ask this.  How badly am I exposed if I have "security = share"?
Can anyone within the range of my router access those shared files?  Would they need to know the name of workgroup at least (it's not the default XP name)?
If the user account you are logged in under locally on your Ubuntu workstation is the same as the owner and/or group that has permissions to use the shared directory, anybody that can see your network can see the samba server name and access that directory with the same permissions. By setting security to share, you have eliminated the need for the remote user to login to access the shared directory. This is in the smb.conf file I posted a couple of days ago in this thread. The only thing standing in the way is the dhcp server issuing an ip address to that unknown remote user. Limit the number of ip addresses necessary to run your lan to the bare minimum. and then make sure all ip addresses are utilized. Otherwise, disable dhcp, and hardcode ip address for each lan node. Also, change all the default settings on your router, especially the password to gain access to router settings. But this is probably more trouble than just securing each node. My original post 's purpose was to intended to help detect hardware or protocol problems. I probably should have specifically said that. Once you have the wide open share working, then work on securing your nodes.

---

### Post by kexodusc on 2007-05-23
> **dolphin_oracle said:**
> These leads back to the user accounts we started tinkering with.  I've been playing with my systems here, and with security=share set up, the only real security my folder had were the system permissions.

just a quick refresher:  the samba_user account must have the same login name and password as a valid system_user account.  These are all case sensitive.  The security layers are the samba permissions (public, writable, etc...) and then the system permissions (-rwx).  

I'm really at a loss here, and I can't seem to replicate your issue.  If in your tinkering you figure out the issue, please post your solution here.

Well, I'm in the process of re-tracing my steps with respect to the walkthrough/how-to's I've tried.

First step I've noticed I could possibly be misinterpreting is the security = user configuration, specifically the smbusers file:

My smb.conf has:
security = user
username map = /etc/samba/smbusers

In my smbusers file I have:
system_username = "ken"
system_username = "loki" 

for the 2 users I'm trying to setup.  
"loki" is the XP laptop.  ken is the ubuntu box.  Maybe I've got that step wrong, should these two users be numbered somehow to distinguish themselves from each other, perhaps:
system_username1 = "ken"
system_username2 = "loki"

maybe the way I have smbusers established now, with "sytem_username" = 2 different users is causing the problem?

Also - another user reported similar problems and suggested it was the Samba update recently that had a bug - he's reported his symptoms have been fixed with a quick second update this week to address that bug:
[http://ubuntuforums.org/showthread.php?t=449991](http://ubuntuforums.org/showthread.php?t=449991)
something about the Force group option no longer working properly in Fiesty.

I'll try this out when I get home, perhaps that's all it was and I wasn't the problem after all :)

---

### Post by kexodusc on 2007-05-23
Well the problem was definitely solved by the quick upgrade  to  samba version 3.0.24-2ubuntu1.2.

All that and it wasn't even me.

Anyway - Dolphin Oracle and djchandler thanks for helping out - I learned alot about samba and networks if nothing else!

Cheers!

---

### Post by dolphin_oracle on 2007-05-23
Doh!

Well, I'm glad you got it working.  I sure learned a lot too!

D.O.

---

### Post by djchandler on 2007-05-24
You're welcome. We all learn something newexchanging like this. So thank you!

---


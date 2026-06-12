---
title: "File Sharing Help? Anyone?"
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by apoc.feuer on 2005-05-27
Dear all, 

I have actually tried to share one folder (I name this folder smb for the sake of discussion) in my linux machine to let my windows client to read/write/access to this particular shared folder.

The funny thing is, when my windows machine is trying to access smb, it prompts for userid and password, which I don't remember I have set it in the first place, can anyone help? Or is there anymore setting needs to be done? I have visit Samba website and their documentation is too much for a newbie like hehe...

Any help will be much appreciated...thanks in advance

---

### Post by TripHammer on 2005-05-27
If your windows machine is getting prompt then that's good, you got samba running at least.  Assuming you set up the shares correctly, it sounds like you just need to setup a user.  Samba user accounts are held separatly from the OS users.  To add new samba user:

smbpasswd -a <username>

you'll be prompted to set the password.  Then for good measure do:

sudo /etc/init.d/samba restart

---

### Post by apoc.feuer on 2005-05-27
Thanks a lot, let me try it out and update on this one... :)

---

### Post by apoc.feuer on 2005-05-27
Thanks, for the advise, but I think I might not know how the terminal works? Because when I type the command in the terminal I get the following: 

----------------------------------------------------------------------------------------------
shawn@ubuntu:~$ smbpasswd -a shawn
When run by root:
    smbpasswd [options] [username]
otherwise:
    smbpasswd [options]

options:
  -L                   local mode (must be first option)
  -h                   print this usage message
  -s                   use stdin for password prompt
  -c smb.conf file     Use the given path to the smb.conf file
  -D LEVEL             debug level
  -r MACHINE           remote machine
  -U USER              remote username
extra options when run by root or in local mode:
  -a                   add user
  -d                   disable user
  -e                   enable user
  -i                   interdomain trust account
  -m                   machine trust account
  -n                   set no password
  -w PASSWORD          ldap admin password
  -x                   delete user
  -R ORDER             name resolve order
----------------------------------------------------------------------------------------------

Or do I need to add a user under System/Administration/Users and Groups before I can a password here? Any suggestion will be greatly appreciated...:)

---

### Post by apoc.feuer on 2005-05-27
Hi, anyway I manage to add a user under root terminal thanks for the earlier advise hehe...but right now I have another problem which is I can't copy or paste files into my linux via windows....any settings that I need to take care of in particular?

I remember that I set my folder option (In the GUI mode) as: allow reading and browsing in the share folder. Is that correct?

---

### Post by Error_Msg on 2005-05-28
======
WARNING
======
I'm as much of a newbie (I hate that word!) as you are but, I think that you need to go to your shared folder in Linux right click >properties>permissions> and check write on "others."

E_M

---

### Post by apoc.feuer on 2005-05-29
Hmm why the warning sign?  O:) Anyway thanks for the advise let me try it out and let me update you guys. Thank you so much  :)

---

### Post by Tass on 2005-10-22
Hi

I had the same problem.  You need to type sudo in front of any commands in the terminal.  Not sure why, if it's the case for everything, etc., but I know it worked for me in this case ("sudo smbpasswd -a <username>", after which it prompted me for a password.

Tass

---

### Post by uselessinfo on 2005-10-24
Hi,

I'm trying to follow the insturctions in this thread, but I'm running into a problem. I'm sure it's probably something simple that I'm overlooking, but I've only been using linux for about two weeks now, so I'm not sure what it might be.

My fiancee and I both have computers. I'm using ubuntu, she's using windows xp. Before I decided to try ubuntu, I was using windows 98, and we weren't having any trouble sharing files. After I switched, and eventually installed samba, I could still access her shared folders. She, however, can't access mine. She's prompted for a username and password, which I haven't set up. This seems to be the same trouble that this thread is covering.

Now when I tried to set up a username and password in terminal, I wasn't able to do so. I decided to set up the username newuser just to keep things simple. When I did so, I was prompted to enter a new password, which I did, and then prompted to retype the password, which I did. The code that I've pasted below shows the message that I received upon doing so.

```
mike@ubuntu:~$ sudo smbpasswd -a newuser
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user newuser. Does this user exist in the UNIX password database ?
Failed to modify password entry for user newuser
```

Any help would be greatly appreciated.

---

### Post by intellidenuser on 2005-11-16
Tass, the sudo command worked! Thanks.

Uselessinfo: 
Two things:

First, try using a different username for your smb login 
(ex: sudo smbpasswd -a <newusername or maybe root??>)

Secondly, try changing your terminal to root:
mike@ubuntu:~$ su -
password: <Your root password here>

now your terminal should look like this:
root@ubuntu:~$

Then try adding an SMB user.

Hope that helps

---

### Post by racecat on 2005-11-16
[QUOTE=uselessinfo]Hi,

I'm trying to follow the insturctions in this thread, but I'm running into a problem. I'm sure it's probably something simple that I'm overlooking, but I've only been using linux for about two weeks now, so I'm not sure what it might be.

My fiancee and I both have computers. I'm using ubuntu, she's using windows xp. Before I decided to try ubuntu, I was using windows 98, and we weren't having any trouble sharing files. After I switched, and eventually installed samba, I could still access her shared folders. She, however, can't access mine. She's prompted for a username and password, which I haven't set up. This seems to be the same trouble that this thread is covering.

Now when I tried to set up a username and password in terminal, I wasn't able to do so. I decided to set up the username newuser just to keep things simple. When I did so, I was prompted to enter a new password, which I did, and then prompted to retype the password, which I did. The code that I've pasted below shows the message that I received upon doing so.

```
mike@ubuntu:~$ sudo smbpasswd -a newuser
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user newuser. Does this user exist in the UNIX password database ?
Failed to modify password entry for user newuser
```

Any help would be greatly appreciated.[/QUOTE]

The user name must already exist as a user on the system (such as mike). Then just type in the desired password. I don't think this has to match your system password. the sudo gives you root permission for that command only. It's a pretty cool tool to keep us from just logging in as root and inadvertantly causing problems. If in doubt, try running commands without the sudo. Some things should be run as a normal user. An error message will let you know if you have to run it as root.

Hope this helps,
Bill

---

### Post by Quacka on 2005-11-21
I have the same problem as the topcistarter.
I shared with samba a few folders in kubuntu.

I try to access these in windows XP -> I get a question for a username/password.

I did use the command "sudo smbpasswd -a <newusername>"
I filled in a password (2 times).
After that I tried to access the shared folders in windows xp. Still the question for a username/password.

Who can help me?

---

### Post by chrisjasper on 2007-02-19
I also had this problem at the start of the forum, after reading it and following the instructions it now works.
Here is what i did:

(As long as you have set up the Shared Folders and installed the sambs and unix file sharing parts).

open a command prompt and type sudo sambapasswd -a yourusernamehere
type the sudo password (your account password) then it will request the new password, its probably easier to use the same password to save remembering multiple passwords.

reset the samba daemon with:

sudo /etc/init.d/samba restart

After that I just connected to the share with my username and password and the workgroup set in Shared Folders (default is MSHOME) and have access to my files from Linux, Mac and XP.

Hope it works for you.

---

### Post by n8bounds on 2007-02-19
this should get you started quickly
[http://ubuntuforums.org/showthread.php?t=365575](http://ubuntuforums.org/showthread.php?t=365575)

---

### Post by Dag J. on 2007-07-25
***@****:~$ sudo smbpasswd -a newuser
New SMB password:
Retype new SMB password:
Failed to modify password entry for user newuser

---


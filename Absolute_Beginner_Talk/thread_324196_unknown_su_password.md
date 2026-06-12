---
title: "unknown su password"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Eldon on 2006-12-23
I just (re)installed Edgy last night fresh from a CD.  It was a full format all-default installation.  Today I applied the available updates then went to the terminal and typed su.  I used the same password as my user account (the one I logged in with after the required reboot, and CAPS was off both times)  and I get a su: authentication failed error.  
I can sudo su and get root access but I don't understand what has happened to su.  2 days ago when I did exactly the same install (same CD too) I had no problem with using su.
Any thoughts would be appreciated.

---

### Post by po0f on 2006-12-23
Eldon,

By default, there is no password for the root account.  You must have added one on your old install accidentally.

---

### Post by moma on 2006-12-23
Hello,

You can activate (unlock) the root account by giving it a passwd. 
This thread explains howto: [http://ubuntuforums.org/showthread.php?p=1283789#post1283789](http://ubuntuforums.org/showthread.php?p=1283789#post1283789)
But it's better to use "sudo". Keep the root account locked.


Merry xmas,

---

### Post by Eldon on 2006-12-23
Thank you for the responses,

I'm not having problems with the root account right now, "sudo su" works fine and it accepts the one password I've used for installing.  Package manager also accepts this password, as does just logging in.  The only thing that won't accept this password is "su".  I'd like to know what happened to the su password (or anything else) that is stopping me from simply using "su" at the command line to get my stuff done.  
I haven't done anything with any users, groups, passwords or anything else.  All I had done was apply the available updates and reboot.
Oh and it was a complete reinstall including a full format of the system drive so (I'm assuming) the previous install shouldn't be affecting anything?

Thanks again

---

### Post by moma on 2006-12-23
sudo asks your normal user passwd.
su asks root's passwd, but the root account hasn't one. It's locked by default.

---

### Post by wdo_will on 2006-12-23
If you want to use a root terminal instead of prefixing each command with 'sudo', you can just type 'sudo bash'.

---

### Post by Eldon on 2006-12-23
Ok  I'll just stick with sudo then.  I don't understand why su with my normal user password worked last install and not on this one but sudo should do everything I need.  (I didn't set a root password last install 2 days ago either)

Thanks again and have a great Christmas!

---

### Post by rbrt73 on 2006-12-24
I'm experiencing the same issue as Eldon, I did a clean install last night then I did an update. Today I installed dvb-utils, dvbstream gxine and mplayer. I used the *su* command in 1 terminal and it worked ok, then I opened another instance of terminal and tried to use the *su* command again and it didn't work. error message: "su: Authentication failure Sorry."

I shutdown, came back later and couldn't get the *su* command to work at all. I tried sudo bash and had some success, but it's not the same. Any idea's people?

---

### Post by rbrt73 on 2006-12-24
I fixed mine by going to System - Administration - Users and Groups - then changing the root password to the same as the regular user that I use. su is working again now.

---

### Post by MkfIbK7a on 2006-12-24
ubuntu seems to try to keep you form ruining your system more than other os's so they dont actually ask for a root password when you install however you can add one by using this script

$ sudo passwd root
passwd: <whatevr>

this gives root a password however you cant log in as root

---

### Post by Sef on 2006-12-24
It is safer to run sudo than root.  Read [RootSudo]("https://help.ubuntu.com/community/RootSudo") to find out why.

---


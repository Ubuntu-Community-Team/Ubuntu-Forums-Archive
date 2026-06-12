---
title: "[SOLVED] Permission, Permission, Phooey !"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-11-25
I just installed AVG for Ubuntu and tried to update the files and got this for my trouble: "Sorry; you don't have permission to update AVG". 

This is not the only time I've been told that I don't have permission to do something.

I am the _ONLY_ user on this machine, so how do I get this so called permission?:confused:

Thanks for any help,

Jon

---

### Post by aysiu on 2007-11-25
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Romin-1 on 2007-11-25
Thanks for the reply aysiu, but that didn't really address the issue.

With AVG Anti-Virus Control Panel open I click on the Update Button and that's when I get the acurssed "You don't have..." bleeping Popup.

How does AVG know I don't have permission? How do I tell Ubuntu I have said permissions? It doesn't even ask for a password.

*What I want is to have full permission to do anything that I darn well want to on this machine.*

 It is a stand alone PC, no dual boot or networked with anything other than the internet.

It is not only AVG, there have been other occasions, in Ubuntu itself, that I have been told that I don't have permission, bla,bla,bla......

At this point I'm of the mind that if I can't get full control of this machine I'm just gonna dump Linux and use it for a paperweight or doorstop.

Jon

---

### Post by aysiu on 2007-11-25
I'm not sure what's going on, as I don't use AVG. Is it possible it needs to be run as root?

What's the command you usually run to start AVG?

---

### Post by Romin-1 on 2007-11-25
I went here  [http://free.grisoft.com/doc/5390/us/frt/0](http://free.grisoft.com/doc/5390/us/frt/0) and DLd and installed the deb package.

Once it was installed I clicked on the icon to open the program. Then I clicked on the button to download the latest definitions. That's when I got stopped by the paranoid Ubuntu. No terminal,command line.

It seems that I have to have some kind of root permission to alter some of the things on this machine. 

How can I gain full control, with full permissions on this Linux only PC ?

I've already accepted the fact that I have to enter a password every time I sneeze but this "You don't have permission,,," is driving me barmy.

Jon

---

### Post by sailor2001 on 2007-11-25
avg is probably in /usr/bin in your computer. locate that then click on properties and click permission

---

### Post by aysiu on 2007-11-25
Not sure if this helps, but you may want to check out:
[HOWTO: Install AVG free anti-virus](http://ubuntuforums.org/showthread.php?t=136064)

---

### Post by Romin-1 on 2007-11-25
Thanks Sailor2001,

Went to usr/bin and got this greeting, "You are not the owner, so you can't change these permissions".  WELL, If I'm not the bloody owner then who the heck is??

Thanks to both you guys for trying. I know I don't need an Anti-Virus per se, really only wanted the email scanner portion anyway. Sooo, gonna dump it.

Really, how do I get full permission, be the owner, to do as I please in this thing, without it thinking I'm some sort of sneak thief?

Jon

---

### Post by PeterJS on 2007-11-25
Root is the owner of pretty much everything outside of /home. One of the things that separates windows from linux is the fact that it does a good job of separating user privileges from system privileges. Since you are the only user of the machine you are by default in the admin group, users in the admin group can run commands under sudo effectively giving that command root privileges. See here for more detail:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
And the documentation on file permissions too:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Under windows everyone runs as an admin account which has direct access to everything, where as every one on linux runs as a limited account, which may be in the admin group, which allows for root access through sudo, but not directly.

You probably want to run the update under sudo as that's the "right way" to do it. If you *really* want to make AVG update-able as a user find all the files that AVG needs to update and change the ownership of the files to the admin group with:
```

sudo chown root:admin <filenames>

```
and then make sure that they are group writeable
```

sudo chmod g+w <filenames>

```

---

### Post by philinux on 2007-11-25
I know this may sound strange but you dont need avg.

But if you want to run it the open a terminal and run 

sudo avg to whatever the program is.

I moved to ubuntu in august from windoze and have not got avg which I had, running.

Its not necessary

---


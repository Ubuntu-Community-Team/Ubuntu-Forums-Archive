---
title: "Administrator permission problem"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by rhibberd on 2007-04-02
I have a problem that I took the administrator permission away from my logon.  I thought that I could log on using the root for the administrator permission, but apparently Ubuntu doesn't allow that.  I can log into the root account in a terminal, but I don't seem to be able to change the administrator permission.  HELP

---

### Post by mikewhatever on 2007-04-02
Normally, users aren't loged in as admins in Ubuntu, so you probably haven't had the rights in the first place. You can get admin rights by preceeding a command with sudo. Suppose you wanted to edit your grub menu, you'd need to > sudo nano /boot/grub/menu.lst

---

### Post by zvacet on 2007-04-03
Go to the recovery mode to become root and type this command where username is your usename and group is admin  
```
 adduser username groupname
```

---

### Post by aysiu on 2007-04-03
Some more details on zvacet's suggestion:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Once you have *admin* privileges back again, this is how you use it:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by ndefontenay on 2007-04-03
I think it would be difficult to deny yourself the right to be admin if you are not admin in the first place.

To issue such a command you need to run the sudo command in front of any command you want to try.

that is required even for reading some files in protected area say etc.

```
sudo vim /etc/X11/xorg.conf
```

This command will prompt you for a password.

Let us know how it works for you :)

---

### Post by zvacet on 2007-04-03
If he is not in admin group how to use sudo?

---

### Post by mikewhatever on 2007-04-03
> **rhibberd said:**
> I have a problem that I took the administrator permission away from my logon.  I thought that I could log on using the root for the administrator permission, but apparently Ubuntu doesn't allow that.  I can log into the root account in a terminal, but I don't seem to be able to change the administrator permission.  HELP

How did it happen that you became unable to sudo?

---

### Post by rhibberd on 2007-04-03
I tried all the different fixes that were suggested.  None of them worked.  All the accounts are user accounts, and not administrator accounts.  Even creating another account just created another user account.  I think I'll just give up, reformat the hard drive and reinstall Ubuntu.  I had thought that Ubuntu was similar to Fedora, that you could do administrative functions in the root  , but after reading about the sudo command, and how you can't really log into root, I decided to redo everything.

Thanks anyway.

---

### Post by aysiu on 2007-04-03
You can log in as root by booting into recovery mode. Why didn't that work?

What happened when you booted into recovery mode and typed this? ```
adduser *username* admin
``` where *username* is an already-existing username?

---


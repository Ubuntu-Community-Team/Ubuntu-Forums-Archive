---
title: "[SOLVED] My user/pass isn't working when connecting to linux box via Samba"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-05-31
I can connect from Ubuntu to Windows just fine, the problem is the other way around.  I can see the Ubuntu box in workgroup and when I double-click on it, the password dialog pops up.  I type in my Ubuntu user/pass and it just keeps popping up the user/pass window.

When I try it from command line:
> net use * \\192.168.0.8\upload /user:name
The password is invalid for \\192.168.0.8\upload.

Enter the password for 'name' to connect to '192.168.0.8': *<password>*
System error 86 has occured.

The specified network password is not correct.

I don't know what else to try, why isn't my password working?

---

### Post by 13thMonkey on 2007-05-31
Which guide did you use to install and setup Samba? The username and password for your shares will be the ones you set in Samba, which may not be the same as your username and password for Ubuntu.

---

### Post by lazyart on 2007-05-31
```
sudo smbpasswd -a *username*
sudo smbpasswd -e *username*
```

Then try again from windows.

---

### Post by marklid on 2007-06-01
Cheers lazyart worked a treat (still finding bits to fix after fresh install of Feisty!)

---

### Post by AncientPC on 2007-06-22
> **lazyart said:**
> ```
sudo smbpasswd -a *username*
sudo smbpasswd -e *username*
```

Then try again from windows.
Thank you.

---

### Post by JSpaceCadet on 2007-07-15
I'd just like to get a chance to say thanks to all who helped and were helped as part of this.  I've joined the "helped" gang.  It's funny though, I don't remember ever having to do this before under RedHat or Fedora - other than setting the password.  It seems like all users were enabled.  Perhaps that was an older version.

One thought here, and I can't possibly be alone in this: Why aren't SAMBA passwords and USER/LOGIN passwords kept synchronized.  I know that part of the SMB protocol allows user passwords across the network, and I think SAMBA implements that feature to some extent (I haven't ever tried it).

Actually, since GNOME/*Ubuntu created the great (seriously) GUI for creating shares (Administration->File Sharing), why can't that module, and the one that handles GUI user password changes report password changes to each other.
OK, I can see where it would be pretty easy to implement a phony smbd that would get reported to which would be a security risk.
Accepting the fact that I haven't thoought through all the conditions - functional, security, etc. can't this process that has been causing problems for 8+ years be streamlined (from within the GUI)?

Again, thanks to all!

Joe

---


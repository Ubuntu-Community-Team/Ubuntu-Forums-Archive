---
title: "Does the share folder GUI work?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by jperkins on 2007-10-22
I'm trying to share a folder to copy files over to my shiny new Ubuntu machine, but I can't seem to log in from the Windows machine.

I've shared the folder from the context menu and selected it as writable, but there was no option for which users to allow and it apparently isn't a public share because it's asking for a user/pass and my login isn't accepted.

Based on the number of threads I found, this is fundamentally broken in older versions of Ubuntu and is only a non-functional GUI.

Does the 7.10 GUI work yet?  That's a pretty basic need for an OS.

Thanks,
John

---

### Post by Dr Small on 2007-10-22
Make sure your firewall allows connections for the IP address of the Windows machine, set a samba password:
```
smbpasswd -a *username*
```
Then restart samba:
```
sudo /etc/init.d/samba restart
```

From the Windows machine, enter in the Windows Explorer Address Bar:
```
\\*ipaddress*\
```

Dr Small

---

### Post by jperkins on 2007-10-22
I tired what you suggested adding sudo smbpasswd -a john, then restarting samba but I still get the same result.

How do I check the firewall?  I don't usually enable one on my individual machines, I use the one on my router.

I had heard that Ubuntu was finally a great desktop Linux, but you still have to use the command line all the time? :(

---

### Post by kah00na on 2007-10-25
Did the "sudo smbpasswd -a *userid*" work?  Whatever "userid" you create with smbpasswd also has to be a real userid on your Ubuntu system.  I had the same problem too for a while.

I created a "tuwanda" user in Ubuntu (System -> Administration -> Users and Groups)
Then ran "sudo smbpasswd -a tuwanda"
I shared out the /home/tuwanda directory.
Then connected to my ubuntu box with \\ip_address
and used userid "tuwanda" and its password to connect and it worked.

If you are sharing a directory that is not the user's home directory (like /uploads), you need to make sure that the Ubuntu userid (like "tuwanda") has at least read access to that directory.

---

### Post by kah00na on 2007-10-25
Also, unless you manually installed a firewall on your Ubuntu system, the required ports should be open.  You don't need to worry about any firewall settings... on the Ubuntu box I mean.

---


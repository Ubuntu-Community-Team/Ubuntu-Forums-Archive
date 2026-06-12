---
title: "Foolproof way to access Windows shared folder"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by acl123 on 2007-12-15
Hi,
I am trying to access a shared folder on Windows computer. I've done this before but it seems to work sometimes and not other times. Right now it's not working.

In Nautilus I type in smb://192.168.1.136/   (eg. the IP of the computer I'm trying to access). It hangs for about 30 seconds then says "sorry could not display all contents of... etc"

I have tried other things - eg. using the name of the computer instead of the IP, or going directly to the name of the shared folder eg. smb://mycomputer/Shared/

The folder is definitely shared - I can access it from another Windows computer.

If I go to "network:///" in Nautilus I cannot see the computer either.

As I said, I've seen the computer and its shared folders before. Just not today.

---

### Post by HermanAB on 2007-12-15
Is your Workgroup defined right in /etc/samba/smb.conf?

Debug things using smbclient.  Nautilus will not show you all error messages and is therefore only useful when it works.

Cheers,

Herman

---

### Post by acl123 on 2007-12-23
Hi, once I've made changes to the smb.conf how do I restart Samba without restarting the computer? Looking around on the web it says to use "/etc/init.d/samba restart" but I don't have samba under /etc/init.d. I tried to locate it but couldn't find it.

---


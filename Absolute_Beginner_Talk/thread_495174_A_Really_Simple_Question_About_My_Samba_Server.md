---
title: "A Really Simple Question About My Samba Server"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by NavmaN on 2007-07-07
Hi,

I recently started a Samba server, and I can connect to it fine from Ubuntu (places, connect to server, etc.) but I can't seem to connect to it from Windows. In Windows Explorer I enter in the address bar "\\IPAddressOfServer\Shared Folder" but it gives me an error message "Windows cannot find \\IPAddressOfServer\Shared Folder"

Is there any Windows web browser that supports the "smb" protocol like Firefox 1.5 in Ubuntu 6.06?

Should I try the local IP address of the server/computer? The IP I'm using currently is the one that was assigned to it by Hamachi.

Note: I'm logged into Hamachi on the Windows box too and I'm part of the network that I created.

BTW, I'm using this tutorial:
[http://nerdica.com/?p=30](http://nerdica.com/?p=30)

Please Help, I'm so so close.

Thanks,
Van

---

### Post by HermanAB on 2007-07-07
In Windoze, is file sharing turned on and enabled in the firewall?
In Linux, is port 445 open in the firewall?

Test connectivity using telnet:
c:\> telnet ip.address.of.server 445

The server should respond with something.

---

### Post by Steven_B on 2007-07-07
This sounds like a permissions settings problem.  Could you post your smb.conf?  (Use "gedit /etc/samba/smb.conf" to view it)

This might also be of use: [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by NavmaN on 2007-07-07
Nevermind everybody, I got it. I had to use the local IP of the computer, i.e. 192.168.0.XXX

Apparently Hamachi is just used to trick the computers into thinking they are both in the same LAN, therefore allowing you to use the local IP (192.168.0.XXX) even when you are not in the same LAN.

Thanks for the help though, I appreciate it.

Van

---


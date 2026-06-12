---
title: "VPN Client question"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-05-18
My school requires a VPN client to connect to its wireless network, and OpenVPN asks me for a "group password" before it can do anything.  The Cisco VPN client for Windows only requires the username and password that I use to logon in the school's computer labs.  I asked someone in the IT department about the group password, and he had no idea what I was talking about. Is there a way to connect to a VPN without putting anything in the "group password" field.

---

### Post by PgR on 2007-05-18
If they're using group authentication, then what the client sees as the password, the firewall it connects to will call a pre-shared key.

It may be that the staff have already imported that into the windows client, so now it just asks for username/password.

You could do worse than to ask the staff for the pre-shared key. Of course, they may not want to tell you...

Failing that if you look at 
c:\program files\cisco systems\vpn client\profiles\<profile_name>.pcf 
it will show either the group password or (more likely) an encrypted version of it.

Good luck.

---


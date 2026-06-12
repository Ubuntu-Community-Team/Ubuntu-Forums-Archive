---
title: "networking problem"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-12-18
ok i want to connect with my windows pc via LAN.

my windows pc has an ip of 192.168.0.1

so when i connect other pcs to it all i do is give them another ip address such as 192.168.0.2  and thats it its done.  but i cant seem to connect my ubuntu laptop this way.

they just dont show up.


so how do i do this guys??    i also did a search on this topic but got more confused after seeing the topics.

---

### Post by jken146 on 2007-12-18
I've never done this myself, but I think what you need is Samba, the network protocol for windows boxes.  Search around for that.

---

### Post by faraz_k86 on 2007-12-18
yes thats the part i need help with??

---

### Post by stump138 on 2007-12-18
open nautilus and try smb://192.168.0.1

it should allow you access to whatever shares you have on the windows machine

---

### Post by faraz_k86 on 2007-12-18
ill try that but isnt there any proper tutorial on networking in ubuntu.

whats the deal with this samba??


and why cant i see anything in my networking manager or in the windows network??

---

### Post by stump138 on 2007-12-18
Samba is a system/set of protocols/however you like to call it :).  It is primarily built to allow windows based clients to connect to linux servers.  Most of the stuff you need to connect to windows based machines are already installed in Ubuntu.

SMB is the pre-cursor to CIFS, which is the file sharing protocol used by microsoft.

You can find tons of information on these setups at [http://www.samba.org]("http://www.samba.org")

You still need to have the shares available on your windows machines. You do this the same way as you would for any share, there is no difference because you are connecting with an Ubuntu based machine.  hope that makes some sense

---


---
title: "windows network computers"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by sp0onman on 2007-10-06
i can see my LAN computers if i type in: smb://"computersipaddress" in nautilus, but how do i just add that computer to network places? so i dont have to type in the ip address everytime i want to move files across the network?

---

### Post by sp0onman on 2007-10-06
bump

---

### Post by MrFSL on 2007-10-06
That's a rather quick bump.

Be patient!

Places > Connect To Server

---

### Post by jimrz on 2007-10-06
> **sp0onman said:**
> i can see my LAN computers if i type in: smb://"computersipaddress" in nautilus, but how do i just add that computer to network places? so i dont have to type in the ip address everytime i want to move files across the network?

go to the top panel > Places > Network, this will open Nautilus which should show you "Windows Network", double click and you first should see each "workgroup" that your box sees on the network then open the appropriate one and you should see your win box

hint: editing smb.conf to make your ubuntu workgroup name identical to your win one makes life easier, especially if using the same user name/password on both boxes

---

### Post by talby on 2007-10-06
I recall having to install winbind "sudo apt-get install winbind" then editing /etc/nsswitch.conf with "hosts:     files dns mdns wins" so my linux box can see my dhcp'd xp pc's...

---

### Post by HemiGTX on 2007-10-07
use SAMBA.. all the info you could need is right on this page here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---


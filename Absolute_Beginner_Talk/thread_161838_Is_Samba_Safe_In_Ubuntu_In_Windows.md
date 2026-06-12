---
title: "Is Samba Safe In Ubuntu? In Windows?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-17
I have just configured my samba share correctly, and I would like to know if it is safe, as in can people look at/edit/corrupt my files through samba.  My linux box has firestarter on and is connected to a router via ethernet cable.  My windows box is connected wirelessly to the router and has windows firewall on (not much of a firewall-eh).  Are both safe?

---

### Post by Monster_user on 2006-04-17
Routers have Firewalls. So it should protect your Samba/Windows network.

*IF* your router gets hacked, then your computer will not be secure. Without knowing how your systems are configured, I cannot say which would be more secure.

Since the Linux box has a good firewall, and has fewer "known" vulnerabilities, I would say it would be more secure.

Just don't set one up to share the connection, and then enable Samba/File Sharing...

---

### Post by user1397 on 2006-04-17
[quote=Monster_user]Routers have Firewalls. So it should protect your Samba/Windows network.

*IF* your router gets hacked, then your computer will not be secure. Without knowing how your systems are configured, I cannot say which would be more secure.

Since the Linux box has a good firewall, and has fewer "known" vulnerabilities, I would say it would be more secure.

Just don't set one up to share the connection, and then enable Samba/File Sharing...[/quote]
What do you mean by "just don't set one up to share the connection, and then enable Samba/File sharing..." by one, do you mean a windows box, or what?

---

### Post by Monster_user on 2006-04-17
I was refering to replacing (or removing) your router with one of the computers. Windows calls it "Internet Connection Sharing". I don't know what the correct Linux, or *nix term is.

---

### Post by user1397 on 2006-04-18
[quote=Monster_user]I was refering to replacing (or removing) your router with one of the computers. Windows calls it "Internet Connection Sharing". I don't know what the correct Linux, or *nix term is.[/quote] Ah!
Now about firestarter and samba, i made an inbound policy for samba and for everyone.
Is this bad? should I change it to something else? and if yes, what?

---

### Post by Monster_user on 2006-04-21
Man I thought I had replied several days ago... I am beginning to hate Shift-Backspace, in Dapper, with Xgl. It logs me out instantly "Ctrl-Alt-Backspace" in Breezy.

Well, I lets try this again.

Run "ipconfig" in a Windows Command promt.

Write down the settings.

Run "ifconfig" in Ubuntu, and write down the settings.

Specifically the IP address, or inet address..

Repeat this for a few days. If nothign changes, then run Firestarter and BLOCK all SMB/Samba connections. Then try to connect to Ubuntu, from the Windows PC.

When Firestarter starts showing SMB errors, right-click, and select "Allow from source".

---

### Post by user1397 on 2006-04-21
[quote=Monster_user]Man I thought I had replied several days ago... I am beginning to hate Shift-Backspace, in Dapper, with Xgl. It logs me out instantly "Ctrl-Alt-Backspace" in Breezy.

Well, I lets try this again.

Run "ipconfig" in a Windows Command promt.

Write down the settings.

Run "ifconfig" in Ubuntu, and write down the settings.

Specifically the IP address, or inet address..

Repeat this for a few days. If nothign changes, then run Firestarter and BLOCK all SMB/Samba connections. Then try to connect to Ubuntu, from the Windows PC.

When Firestarter starts showing SMB errors, right-click, and select "Allow from source".[/quote]
Thanks for the reply. I'll try what you said and post back later.

---

### Post by user1397 on 2006-04-21
Thanks! my samba share works beautifully now

---


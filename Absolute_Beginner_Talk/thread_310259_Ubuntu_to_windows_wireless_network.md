---
title: "Ubuntu to windows wireless network?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2006-11-30
I have a second PC running Windows XP as well as this one running Ubuntu and I was wondering if there's a way to set up a wireless network between the two (or the router and them, whatever is fine).

I'm a complete newbie when it comes to networks and haven't got a clue where to start from.. I'm just looking to transfer things between the two (one has a DVD burner and the other doesn't).

Thanks for any help.

---

### Post by wieman01 on 2006-11-30
First of all, both computers can connect to the same router, no problem. That does NOT mean, however, that they can share file or information. In order to enable file sharing, you need to install "samba" on your Ubuntu machine. The package can be found in Synaptic... and there a tons of HOWTOS in the forum.

---

### Post by styracosaurus on 2006-11-30
They both have wireless hardware and you have a wireless router?

If this is the case, and you are able to get to the greater internet with the Linux PC, you should be able to use Samba to share files and printers. My experience in Ubuntu has been great, I didn't have to configure anything.

In KDE, in Konquerer, if you type "smb:/" in the address bar you should be able to see Windows networks. I'm not sure about in GNOME, but I do remember it being this easy. Poke around in Nautilus, there might be something similar. Or in the "System" or "Computer" menu item, there is something like that in KDE, and I think so in GNOME too.

If you can't get to the internet with the wireless Linux PC... that is another story. I'm stuck! I'm a n00b at setting stuff like that up by hand too.

---

### Post by DiJEH on 2006-11-30
I'm not sure about Samba, can it be secured?

---

### Post by wieman01 on 2006-11-30
Secured, yes. You can assign usernames & passwords. The traffic from one computer to another is not secured... So you only have authentication, not encryption. That's not a problem is your local wireless network is encrypted (e.g. WPA). However, if you still prefer encryption, I would opt for SSH or S-FTP instead. But these are way harder to set up.

---

### Post by DiJEH on 2006-12-01
I searched for Samba but nothing turns up.

Installed it through syn and can't find it in any menus either. :(

---

### Post by styracosaurus on 2006-12-01
I may be trying to do this a dumb way... but someone can correct me.

What version of Ubuntu are you running, and with what desktop environment? If you installed vanilla Ubuntu with GNOME and let it handle installing the enviroment for you it should be a question of opening up Nautilus and browsing to remote places. I use KDE, installed when I installed Kubuntu, and it set it all up for me. It was brilliant! Opened up the system menu and there was "remote places" sort of like one might expect from a WinXP machine. I can browse the other computers' shares, but I haven't tried printer sharing yet. Authentication might need some more set up. I am also using 6.10, so maybe in previous releases it was not so fully configured for you.

---

### Post by DiJEH on 2006-12-02
I'm running Dapper and I installed everything default straight off the live CD.

Really I was looking for a nice little guide which would tell me how to set up both of them rather than just Ubuntu, but figured I'd start here before I touched Windows.

---

### Post by wieman01 on 2006-12-02
There is a nice howto on Samba: [http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605")

---


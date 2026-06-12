---
title: "Clipboard Utilitiy for Ubuntu please?"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by qplumb on 2005-11-30
Hi new to Ubuntu and am looking for a similar program to utilize the clipboard for cut and paste.For xp I use clipmate available from [www.thornsoft.com](www.thornsoft.com) 
Also if anyone would like an invite to GMail please email or pm me.
Thanks John

---

### Post by sambler on 2005-11-30
See:

[http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)

Scroll down to "How to install Clipboard Daemon for GNOME?"

Here's a cut and paste from the guide:

-------------------------------------------------------------------------------------------

Read general_notes

wget -c [http://frankandjacq.com/ubuntuguide/gnome-clipboard-daemon-1.0.bin.tar.bz2](http://frankandjacq.com/ubuntuguide/gnome-clipboard-daemon-1.0.bin.tar.bz2)
sudo tar jxvf gnome-clipboard-daemon-1.0.bin.tar.bz2 -C /usr/bin/
sudo chown root:root /usr/bin/gnome-clipboard-daemon
sudo chmod 755 /usr/bin/gnome-clipboard-daemon
sudo gnome-clipboard-daemon &

System &#8594; Preferences &#8594; Sessions

Sessions

Startup Programs Tab -> Add
Startup Command: gnome-clipboard-daemon
Order: 80

-------------------------------------------------------------------------------------------

Hope this helps.

---

### Post by rooster on 2005-11-30
[QUOTE=qplumb]
Also if anyone would like an invite to GMail please email or pm me.
Thanks John[/QUOTE]

Or use [this link]("http://isnoop.net/gmail/") for it...

Rooster

(you can donnate your invitation to them, also)

---


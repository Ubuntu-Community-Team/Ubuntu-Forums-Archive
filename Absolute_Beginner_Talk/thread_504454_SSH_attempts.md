---
title: "SSH attempts"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-07-19
looking through my Firestarter ive noticed 2 random IP addresses blocked trying to access my computer via SSH.

is this serious?

---

### Post by skymera on 2007-07-19
also, i cant resize my home partition size :(

i make my Root smaller.
and put the free space in the Extended partition
(extended consists of Swap and Home)

i move my swap to leave my free space then my Home.
but i cant move my Home EXT3 backwarsds in to the space :(

anyone know how  ican do it?

---

### Post by Malibu Illusion on 2007-07-19
If you're running an SSHd on default port 22, I recommend changing it to something else.  There's lots of drones out there that can, potentially, attempt to brute force your box if you leave it on the standard port.  So, change it, or install something like fail2ban.  If you're not running an SSHd, just ignore it.  They're hitting off a closed port anyway as there's nothing there to listen for their connection.

---

### Post by skymera on 2007-07-19
i am using SSH and yes its port 22 =|
how do i change to a differ port?

any reccomended prts?

---

### Post by Malibu Illusion on 2007-07-19
Type this into a terminal: (replace vi with your text editor of choice...nano, gedit, kate, whatever.  Replace "sudo" with "gksudo" (GNOME) or "kdesu" (KDE) if you're using a graphical app.)

```
sudo vi /etc/ssh/sshd_config
```

Change the port to something like, idk, 2200 or something that is unused.  Then:

```
sudo /etc/init.d/ssh restart
```

Sorted.  You can then remotely connect to your box with:

```
ssh -p2200 username@host
```

---

### Post by joselin on 2007-07-19
Or you can try things like this:
[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

---


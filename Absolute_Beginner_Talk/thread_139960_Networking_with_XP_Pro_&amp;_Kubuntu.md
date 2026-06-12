---
title: "Networking with XP Pro &amp; Kubuntu"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by ironmaiden6669 on 2006-03-05
Sorry to ask this but, how do I network a kubuntu system with a windows xp system ?
I have two pc's.
1) A kubuntu system that I connect to the internet with a dial-up analog modem.
2) An XP system
Both pc's have a 10Mb/s pci ethernet cards and are directly connected to each other with the old BNC type cable. So the hardware is there (if correct).

I have not yet been able to get them to recognize each other.

What I want to do is to connect to the internet via the modem with my kubuntu pc and be able to browse, etc.. on my XP system via the network. Also share a folder on each pc.
I am reasonably new to linux and before a few weeks ago was only experienced in windows/dos. I do have a little experience with network settings in xp, but I have never set up a network before.
I am not comfortable with doing this on a command line. I have followed the online directions to enable root to log on graphically, so I can do everything through the gui system settings.

So back to the original question...
What settings do I have to mess with to make this all happen ?

---

### Post by Ocxic on 2006-03-05
enabling the root user is not recomennded and most of the time, if you need the command line you'll have to use the command line theres no getting around it. and any admin app will oresnt a password if you need root access.

but anyway, using teh network setup wizard in windows, setup your network, and share whatever files and folders you want to share.

and on ubuntu go to Places->connect to server  select windows share from the menu, add the extra info you'll need and hit connect.

I've nerver used a BNC connection so this may or may not work.

you shouldn't need root access for any of this, so don't login as root.
The command line is an intigrated part of ubuntu, theres just no gui for alot of the things you do in linux and half the time, you'll be editing config files, which would be 10x faster to type, sudo gedit /etc/fstab then to manually click around to the file in nautilus and open your editor, as root. plus it's good to know the command line in case you computer gets all wacky, and you don't have the option of using the gui. wich can and does happen to poeple even me.

---

### Post by CameronCalver on 2006-03-08
Hey I want to share internet with my ubuntu computer and a windows xp laptop and when i go places then conect to server it has server,optional information,share,folder,username,domainname,and name to use for this connection and all i want to do if share internet is there an easy way?

---


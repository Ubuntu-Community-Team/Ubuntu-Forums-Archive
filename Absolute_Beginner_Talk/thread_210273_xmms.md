---
title: "xmms"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by SimzI on 2006-07-06
Hi all. 

I have installed ALL my codecs etc and MP3 play works in movie player.

However, I can't get any MP3 to play in xmms and this is really annoying!

Thanks for replies in advance.

---

### Post by bwayman on 2006-07-06
Join the  club. I would like to know as well.

---

### Post by Jose Catre-Vandis on 2006-07-06
Work your way through this page, and report back :-)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

or install Automatix, choose all the codec stuff

[http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix)

---

### Post by jayemef on 2006-07-06
The Ubuntu Guide has instructions on setting up XMMS here: [http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Player_.28XMMS.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Player_.28XMMS.29")

---

### Post by SimzI on 2006-07-06
Right I've done everything, followed the guide and used automatix and it still doesn't play.

What the heck is wrong?! :D

---

### Post by Bull Moose on 2006-07-06
[QUOTE=Jose Catre-Vandis]Work your way through this page, and report back :-)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

or install Automatix, choose all the codec stuff

[http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix)[/QUOTE]


Great direction here.  Thx:)

---

### Post by SimzI on 2006-07-06
Mine doesn't work at all.. I've done everything I've found on different forums and the web but still no luck.

---

### Post by christhemonkey on 2006-07-06
Is it playing but you cant hear it? 
Or just not playing full stop?

Does it output any error messages?
Do you have sound with any other applications?

---

### Post by SimzI on 2006-07-06
It's not playing full stop.
Mp3 and everything else works in all other media apps. :S

---

### Post by woedend on 2006-07-06
does it give you any error messages?  What happens when you push play?  Does it appear to be playing at all or just nothing happens?  Are they on a local partition or networked?

---

### Post by simonn on 2006-07-07
Open a terminal, what does:

```

$ ls /usr/lib/xmms/Input

```

Return?

---

### Post by SimzI on 2006-07-07
They are playing over a LAN and there is no error message. When I press play nothing happens.

---

### Post by woedend on 2006-07-07
what protocol are you using?
if the files aren't mounted locally thats most likely your problem.
for example, if you were using samba/other networking utility to see another computer's share on the network, and double click to play, it will not work because xmms and its offshoots do not support that protocol.  Try dragging one mp3 to your home folder, then playing with xmms...does that work?
The solution is to use smbfs to make the remote pc's share appear "mounted" locally...this will let xmms play it.

---

### Post by SimzI on 2006-07-07
Hi woedend,

It works now that the file is in my home folder. I will look into smbfs.

Thanks.

---

### Post by SimzI on 2006-07-07
I seem to be having a problem with smbfs.. I keep getting:

```
 root@ubuntu:~# mount -t smbfs //rickserver/Server-D/mp3 /home/rick
mount: wrong fs type, bad option, bad superblock on //rickserver/Server-D/mp3,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so 
```

How do I resolve this?

---

### Post by christhemonkey on 2006-07-07
```
sudo apt-get install smbfs 
```

Always helps :)

---

### Post by SimzI on 2006-07-07
Hehe, yes, I thought it was installed with Ubuntu.

However, I'm now getting a different error message:

rick@ubuntu:~$ sudo mount -t smbfs //rickserver/Server-D/mp3 /home/rick
Password:
18378: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

---

### Post by christhemonkey on 2006-07-07
Try specifying rickservers ip adress instead of ricksever.
```
sudo mount -t smbfs //ip.add.rick.server/Server-D/mp3 /home/rick 
```

I would reccomend not mounting it to your homefolder though, as all stuff there will then be inaccesible.
I have a public folder mounted with all my mp3s in /home/public.

---

### Post by SimzI on 2006-07-07
Hi christhemonkey,

I tryed your command and it returs with this error:

rick@ubuntu:~$ sudo mount -t smbfs //192.168.0.6/Server-D/mp3/ /home/public/
Password:
23713: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

*To clarify. This is what I shoould be doing to be able to play remote MP3's in xmms ja?*

---

### Post by christhemonkey on 2006-07-07
```
sudo smbmount 192.168.0.6/Server-D/ /home/public 
```

Something like that maybe?

Are you sure that the share name is Server-D?
Remembering that it is case-sensetive.

---

### Post by Bloch on 2006-07-07
xmms is very crackly when playing some mp3s on my system. An internet search reveals this is a common problem, and there is some consensus xmms is buggy.

It's a beautiful player but the developers have moved on to xmms2
If iy plays mp3s with no problems, then stick with it.

---

### Post by SimzI on 2006-07-08
Hi guys,

I've managed to get it working. I vnc'ed to my server and I disabled sharing the hard drive on the network.I then shared the mp3 folder so the destination ip was //192.168.0.6/mp3 and the command:
 
rick@ubuntu:~$ sudo mount -t smbfs //192.168.0.6/mp3 /home/public

worked.

Bloch, turn the player volume down to about 50 and then control the volume on your speakers/headset.

Thanks for all the help guys, aprecciate it. <3 :)

---


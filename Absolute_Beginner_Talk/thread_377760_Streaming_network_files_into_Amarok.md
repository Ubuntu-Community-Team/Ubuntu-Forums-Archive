---
title: "Streaming network files into Amarok"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by GrantShoe on 2007-03-06
So my computer is setup with a Network Attached Storage drive on the router so that I can share my files with my other computer and my roommates.  I specifically use it to share music but i can't seem to get that working in Kubuntu, specifically Amarok.

I can browse to the files:
System Menu - Remote Places - samba shares - NAS - Music

and i can see all the files.  but when i try to play it in kubuntu, it freezes amarok.  Do i have to mount the drive? (how do i do that?)  can i also have a link to that music folder on my desktop?

---

### Post by GrantShoe on 2007-03-06
ok, after searching and browsing around i see that amarok can't handle networked files and i need to mount the folder.  So I installed samba:
```
sudo apt-get install samba smbfs
```
and then i made a file on my desktop called NAS-music.
now i'm trying to mount the networked folder to the one on my desktop.  it's giving me an error.
i'm running:
```
sudo mount -t smbfs //NAS-250/music /home/grant/Desktop/NAS-music
```
and the error:
> 10593: session setup failed: ERRSRV - ERRbadpw (Bad password - name/password pair in a Treee Connect or Session Setup are invalid.)
SMB connection failed.

i figured at first that i'm typing the wrong admin password in but i tried it a couple times and it's still giving me this error even when i type that in correctly.

---


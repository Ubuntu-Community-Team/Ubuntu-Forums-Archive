---
title: "Xubuntu -&gt; samba"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by andy90 on 2007-04-05
Hi, pretty new to linux and playing around and ive come accross one problem that has had me stumped for two weeks now.

Sorry this is a bit long, but i want to make sure i cover all topics as its not a straight forward build.

Setup 
Ubuntu Edgy 6.1
...running VMware server...
...with a [Xubuntu Lamp VM](http://canned-os.blogspot.com/2006/10/grandmas-lamp-its-easy-enough-for.html) (fantastic so far).

The Xubuntu VM is for ampache (a jukebox) so i need to mount the hdb (vfat) in ubuntu host to the xubuntu guest.

The hard drive is working in ubuntu and mounted as /media/music

The folder /media/music is shared with 777 persmissions

-If in **ubuntu** i press alt+f2 and enter 'smb://192.168.0.5/music' then it shows me the folder :)

-If i boot to **ubuntu** on another computer and do the same it works fine :)

-If i load the **xubuntu** OS and do this i am told "no such file or directory" :(

-Ubuntu and Xubuntu can both ping each other on the 192 address, so the network is fine.

In Xubuntu I have run 
_sudo apt-get install build-essentials samba smbfs_
successfully and it reports that its all up to date.

Question - how come Xubuntu cant see the smb share ?  And when it does this should be ok to mount on startup for xubuntu ?

I am desperate for help, as i say two weeks now and going to scream lol.

Any help muchly appreciated
Thanks in advance.

Andy

---

### Post by andy90 on 2007-04-06
Never mind, resorted to using DSL and xampp instead.

Thanx anyways.

---


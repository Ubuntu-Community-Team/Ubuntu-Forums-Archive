---
title: "Installing vmware player"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-08
Cheers,

I am trying to follow the instructions given at
[https://help.ubuntu.com/community/VMWarePlayerAndWindowsHOWTO](https://help.ubuntu.com/community/VMWarePlayerAndWindowsHOWTO)

but when I did:
sudo apt-get install vmware-player

I get this error:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vmware-player

So I tried installing it via Automatix but after installing and typing in
vmplayer windowsxp.iso

I get 
bash: vmplayer: command not found

Surely I did something wrong here, but I dont know what.  Could someone be kind enough to point me into the right direction.

Thanks

---

### Post by Kirky_D on 2006-10-08
You need to add extra repositories

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by anaconda on 2006-10-08
Or install VMWare server.. here is a howto:
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto)
It is more difficult to install than the player, but it is more complete.. with server you can also make the virtal machines.

And all I had to do was follow this instruction and everything worked ok..

---


---
title: "need help file sharing on a Network"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by morage_key_ring on 2007-07-22
Hi ppl, 

I tried to search on the forum but have not been successful. 

Please can someone point me in the right direction :

my Ubuntu runs on the internet ok, and it's connected to a router; which is also connected to 2 macbooks and a windows XP machine. My question is how do I enable file sharing on my Ubuntu machine so that i can copy files between it and the macbooks / xp machine?

I'm pretty new to linux so i'd appriciate any help, and probably need pretty detailed non-technical advise.  

Cheers,

---

### Post by xpod on 2007-07-22
You`ll probably need "samba" to share between Ubuntu & Windows i think but i`ve never used it myself,no need really.

[https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)
[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28ssh%29](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28ssh%29)

For the macs,i think you could possibly use NFS, which is what i use between Linux machines but dont quote me on that.
You could also use ssh(secure shell)  but you `ll really need to read up on it all as i`m not the guy to explain this stuff in detail..

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29](https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29)

---


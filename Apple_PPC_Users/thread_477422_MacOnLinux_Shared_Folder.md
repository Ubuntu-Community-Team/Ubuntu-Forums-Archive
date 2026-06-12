---
title: "MacOnLinux: Shared Folder?"
date: 2007-06-18
forum: Apple PPC Users
---

### Post by mph66 on 2007-06-18
Hi All,

Would someone please walk me through setting up a shared folder so that I can share files between the Mac and Linux desktops?  I'm confused whether I should start on the Mac or Linux side.

Thanks,

Marc

---

### Post by dannyboy79 on 2007-06-19
well it really depends if you want your linux computer to be a samba server or not? if so, then simply go to System, Admin, SHared Folders, tehn this should trigger the install of samba. then chose which folders you would like to share. then close that dialog box. then see if you can access those shares from the mac.

for sharing folders within mac osX, please see this link; [http://ubuntuforums.org/showthread.php?t=304131&page=7](http://ubuntuforums.org/showthread.php?t=304131&page=7)
then read post number 61.

don'ty forget about firewall issues, that will prevent you from sharing if you setup any firewall on linux (firestarter/iptables) as far as the mac, I beleive that when you follow the link, and do what it says, it should open the neccessary ports for sharing.

---

### Post by nocturn on 2007-06-19
> **dannyboy79 said:**
> well it really depends if you want your linux computer to be a samba server or not? if so, then simply go to System, Admin, SHared Folders, tehn this should trigger the install of samba. then chose which folders you would like to share. then close that dialog box. then see if you can access those shares from the mac.




Can't OS X do NFS (v3 or 4)?  That would be better on *nix

---


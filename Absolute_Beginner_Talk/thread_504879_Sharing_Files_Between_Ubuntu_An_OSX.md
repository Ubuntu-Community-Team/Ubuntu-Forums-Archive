---
title: "Sharing Files Between Ubuntu An OSX"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Armman on 2007-07-19
How do I share my files on my Ubuntu system so I can access them on my iMac?

---

### Post by Digitallysick on 2007-07-19
go to system> Administration> Shared folders, then make sure your setup on MSHOME or WORKGROUP (or whatever it is you use, most people its mshome) and then select the folders you want to share i use "windows sharing" smb

---

### Post by Armman on 2007-07-19
Thanks for the reply I'll try it.

---

### Post by annda on 2007-07-19
theoretically you right-click a folder and select 'share folder'. choose samba, because OS X doesn't support NFS. this should prompt you to install samba.

here you can find out out how to access the shared folder on your mac:
[http://guides.macrumors.com/Networking_Windows_with_Mac_OS_X](http://guides.macrumors.com/Networking_Windows_with_Mac_OS_X)

however, it didn't work for me. if you are successful, please post back. my mac won't connect even to my web server on the local network, so i suppose something is wrong with my mac configuration, not the guide or samba networking under ubuntu.

---

### Post by Armman on 2007-07-19
I tried that and my Ubuntu computer showed up on my iMac. Then when I tired to connect to the shared folder a message came up saying "the alias could not be opened because the original item could not be found" any ideas?

---

### Post by willfriedwald on 2007-09-06
hey - I tried this and had the exact same situation - the linux system shows up in the mac network, but then when I try to connect, I get the same message: "the alias 'linux' could not be opened because the original item can not be found.'

has anyone come up with a solution for this?

for a few seconds I was hopefully - that I could actually access the linux files through the Mac without having to go through SAMBA (which I haven't even tried to do yet...)

anyhow, am curious if there's a way to do it - SAMBA looks incredibly complicated, even though I appreciate that whoever developed it came up with a musical name!

will

---

### Post by Digitallysick on 2007-09-06
On the mac, go to applications, utilties , directory access,  once its open select "smb/cif" make sure its checked, click the lock, enter your pass, click on smb and click configure, and put in    MSHOME

on the linux side, go to system, admin, shared folders , add the folders you want, select windows sharing , on gerneral properties, type in MSHOME for the domain/workgroup

---


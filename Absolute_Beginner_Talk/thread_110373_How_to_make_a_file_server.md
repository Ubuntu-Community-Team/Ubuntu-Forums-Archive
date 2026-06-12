---
title: "How to make a file server"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by hennaheto on 2005-12-30
I basicly I dont know anything abut linux, but i wanted to give it a try.  I have an old tower i use as a file server and I put ubuntu on it, but how do I share the drives?  There will be 4 hard drives connected via crossover into my other tower.  The other tower is running win xp home (photoshop, illustrator, and indesign arent on linux yet).  How do I set it up so i can access and modify the files on the ubuntu system from my xp system?  Thanks!

---

### Post by herrpoon on 2005-12-30
Hi, I think the best way to achieve something like this (the way I do it anyway) would be to setup samba so you can share your files between your ubuntu box and your windows box.  It works up just the same as "My Network Places" in Windows and works very well.    Try the following guide:[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29) as a starter.

---

### Post by juuri on 2005-12-30
hi hennaheto,
with Samba you can share your files with other osses as ms-win and mac os
how u do this exactly i would have to check out myself again - it's been a while

bye

---

### Post by hennaheto on 2005-12-30
when going through that link in the "mounting a samba share" section i get the error "Package smbfs not avaible, but is refered to by another package.  this may mean that the package is missing, has been obsoleted, or is only avaible from another source."  the commands i ran were "sudo apt-get update / sudo apt-get install smbfs" and i got the error message on the last command.  Thanks for the help and the quick replies.

---

### Post by juuri on 2005-12-30
i tried it out by myself and it worked perfectly

i don't know if you have to have it because the link told it was for programs not using GnomeVFS

so long

---

### Post by hennaheto on 2005-12-30
[QUOTE=juuri]i tried it out by myself and it worked perfectly

i don't know if you have to have it because the link told it was for programs not using GnomeVFS

so long[/QUOTE]
sorry but i dont get it ;)

---

### Post by lleb on 2005-12-30
[QUOTE=hennaheto]when going through that link in the "mounting a samba share" section i get the error "Package smbfs not avaible, but is refered to by another package.  this may mean that the package is missing, has been obsoleted, or is only avaible from another source."  the commands i ran were "sudo apt-get update / sudo apt-get install smbfs" and i got the error message on the last command.  Thanks for the help and the quick replies.[/QUOTE]


ok, why are you install smbfs, that would be for mounting windows shares to your linux box, not the other way around?

samba is the way to go, but you need to get it setup, make sure iptables (firewall) is not blocking the smb port (forget what they are off the top of my head) and then from your windows box, mount them like you would any other mount:

open My Network Places
click on tools
mount network drive (something to that effect)
for the path type in something like this:

//192.168.1.100/share

just like you would for any network device you want windows to connect to remotely.  now keep in mind you will have to setup smbuser to match the user name and p/w of your windows boxes so they will have the permissions to access the files on the samba server.

hope that helps some.

---

### Post by juuri on 2005-12-30
sorry hennaheto

i think you

a] don't need the smbfs package - see above

b] should activate the additional repositories. See [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) if you want to know ~
so dl won't fail again!

c u

---

### Post by ottothecow on 2005-12-31
Sometimes SMB gets a little messy though it is definately the easiest solution.

Now that microsoft Services for Unix (SFU) is free, you could try mounting NFS shares as well and compare preformance of the two options.

---

### Post by hennaheto on 2006-01-01
so i have been working on this and i can across a lot of packet loss between the windows box and the linux box.  My windows system reports 50% packet loss and the linux box says 65%.  They are connected via a crossover, the windows box currently has no firewall, and from the windows box to the router is 0% packet loss.  Is there something i should change? is this normal?

---

### Post by lleb on 2006-01-02
do you have any extra ports on the router (is it a current SoHo 4port switching router like a Linksys or D-link) or do you have a HUB/Switch in the LAN you can use instead of X-over cable?

no that kind of PL is not normal.  with the X-over cable connection, what is the IP scheme and full stack you are using, it is possible you have that configued improperly.  If you are doing so via DHCP what computer is the DHCP server?

in other words we need way more info about your LAN and the connection between the linux and windows systems to really help and answere these questions.

---

### Post by ComputerExpertVK on 2007-08-27
Yeahejch!!!
Thanks A Lot Ppl!!!
Rofl!!!
Helped A Lot!!!

---


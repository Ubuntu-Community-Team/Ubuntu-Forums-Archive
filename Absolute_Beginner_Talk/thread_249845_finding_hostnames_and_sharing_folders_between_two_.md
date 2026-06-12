---
title: "finding hostnames and sharing folders between two Ubuntu systems"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-09-03
I have installed sshfs and as far as I understand, "connect to a server" in the locations menu is the place from where I could connect to the other computer. If only I knew what is the server address and how to make a computer server to be accessed. And how to share particular folders.
Samba seems nice and easy enough, when you have used "My Network Places" in Windows - but why can it be used only for Windows networks? Why not make an equally easy application for sharing between two Ubuntu systems? Or does it already exist and I haven't found it?

---

### Post by &#12465;&#12452;&#12488; on 2006-09-03
Open a terminal and run ifconfig, it'll list your network interfaces and IP addresses.

---

### Post by 1002285 on 2006-09-03
Thank you, now I know the addresses. But still, how to set the permissions?
I tried sshfs allow_other ml3@192.168.2.5
where ml3 is my user on the other computer and 192.168.2.5 is the address of the computer, but I only got
"missiong host".
Where's the place to set the passwords etc?

---


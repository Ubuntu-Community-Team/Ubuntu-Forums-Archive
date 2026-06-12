---
title: "Windows error on Ubuntu????"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-08
Hey I've got samba working to share between XP and Ubuntu i can see the ubuntu stuff on my XP desktop computer. But i wanted to see the windows stuff on this comp so i went to Places-->Connect to server

Selected windows but what is the other stuff, and is this even how to connect to windows over a network?

i entered some basic info like

Server = madaduds (network group)
Folder = Adam Toews (shared folder i wanted)
User Name = adtoes (my XP username)

I got this error:

[ATTACH]4287[/ATTACH]

---

### Post by amohanty on 2005-12-08
> Server = madaduds (network group)

What does "network group" here mean?

---

### Post by detyabozhye on 2005-12-08
have you tried Alt+F2 (Run Application), and typing "smb://nameofnetworkcomputer"?

---

### Post by adduds on 2005-12-08
that's the name of my windows network

---

### Post by Joe_CoT on 2005-12-08
have you tried connecting directly to the share, and using guest as the username?

---

### Post by schdefan on 2005-12-08
Not to bother you but have you defined a shared folder? 
Also check if Windows firewall is not blocking!
schdefan

---

### Post by adduds on 2005-12-08
[QUOTE=detyabozhye]have you tried Alt+F2 (Run Application), and typing "smb://nameofnetworkcomputer"?[/QUOTE]

THANK YOU SO MUCH MAN IT WORKED :) YOU'VE MADE MY DAY :) and PROBABLY TOMMOROW ASWELL

---

### Post by detyabozhye on 2005-12-08
Doitashimashite (You're Welcome)! ^___^

---

